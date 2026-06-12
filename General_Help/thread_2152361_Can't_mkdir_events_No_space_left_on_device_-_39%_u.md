---
title: "Can't mkdir events No space left on device - 39% used"
date: 2013-06-07
forum: General Help
---

### Post by gregom on 2013-06-07
noob here... Ubuntu 12.04.2 LTS 64bit. 

I have a 4.5 TB RAID-5 array that I created an EXT4 volume with a bytes per inode count of 32768. It's only 39% used but I can't write to it anymore... Running dumpe2fs -h I see there are still 17044250 free inodes. Why the heck can't I write to the thing anymore?

```
root@testdvr7:~# dumpe2fs -h /dev/sdbdumpe2fs 1.42 (29-Nov-2011)
Filesystem volume name:   <none>
Last mounted on:          /var/cache/zoneminder/events
Filesystem UUID:          0e5aef72-758b-4c4e-b31d-2b26a395e4f2
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype n                      eeds_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nli                      nk extra_isize
Filesystem flags:         signed_directory_hash
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              137351168
Block count:              1098792960
Reserved block count:     54939648
Free blocks:              743645523
Free inodes:              17044250
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      762
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         4096
Inode blocks per group:   256
Flex block group size:    16
Filesystem created:       Fri May 17 10:08:46 2013
Last mount time:          Tue Jun  4 13:26:17 2013
Last write time:          Tue Jun  4 13:26:17 2013
Mount count:              3
Maximum mount count:      -1
Last checked:             Fri May 17 10:08:46 2013
Check interval:           0 (<none>)
Lifetime writes:          1670 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      c3246ef1-2e0f-478a-9017-79b096265ab3
Journal backup:           inode blocks
Journal features:         journal_incompat_revoke
Journal size:             128M
Journal length:           32768
Journal sequence:         0x0007bdf9
Journal start:            15734



```

---

### Post by tgalati4 on 2013-06-07
I presume that zoneminder/events is a bunch of video clips from your security cameras?  Perhaps delete a few and see if that helps.  You might have run into a zoneminder or a /var/cache limit instead.

I'm not familiar with the details, but perhaps there is something in *slabtop*.

```
man slabtop
sudo slabtop
```

---

### Post by gregom on 2013-06-11
Well i've discovered I am actually using all available inodes. I thought setting a custom bytes per inode when creating the volume was going to resolve this issue but it hasn't. I'm not sure how to proceed now... i'll have to do more research.

---

### Post by CharlesA on 2013-06-11
The only way I know of increasing the number of inodes is to reformat that partition. That might not work if you have a ton of data to copy off the device.

---

### Post by gregom on 2013-06-12
i'm fine with that... i just don't know what size of bytes per inode to format with. Obvious 32768 is not working out for me because all inodes are used and i've still got 61% of free disk space! Obviously the math I got was wrong; bytes per inode = (Block size) * (Block count) / (Inode count).

Average size of my JPEG's is between 8 and 17 Kbytes... how do I determine the appropriate bytes per inode to format with on a 4.5 TB volume?

---

### Post by CharlesA on 2013-06-12
I've always left it at the default when I create the file system and so far I haven't run into problems on my 4TB RAID5 array.

---

### Post by gregom on 2013-06-13
It was at default on my first attempt and I ran out of disk space at the same point, 39% use.

What about using ext3 file system? Would that make a difference? We never had this problem with ubuntu 8.04 LTS and it was using ext3 but with the same 4.5 TB volume.

---

### Post by CharlesA on 2013-06-13
The file system shouldn't matter.. I've been using EXT4 for a while now and haven't run into any problems.

Have you run fsck on that drive? Run this and see if it matches up with what dumpe2fs says:

```
df -i
```

Here's the results of dump2fs from my array:

```
dumpe2fs 1.42 (29-Nov-2011)
Filesystem volume name:   RAID
Last mounted on:          /array
Filesystem UUID:          05c730b5-680d-4d33-8e2e-76947d7a93fa
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              244178944
Block count:              976713841
Reserved block count:     0
Free blocks:              92899058
Free inodes:              243194216
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      791
Blocks per group:         32768
Fragments per group:      32768
[COLOR="#FF0000"]Inodes per group:         8192[/COLOR]
[COLOR="#FF0000"]Inode blocks per group:   512[/COLOR]
Flex block group size:    16
Filesystem created:       Tue May 11 21:50:27 2010
Last mount time:          Sat Jun  1 09:42:56 2013
Last write time:          Sat Jun  1 09:42:56 2013
Mount count:              6
Maximum mount count:      36
Last checked:             Sat May 18 14:37:09 2013
Check interval:           2592000 (1 month)
Next check after:         Mon Jun 17 14:37:09 2013
Lifetime writes:          17 TB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      87d5403b-ec28-46cf-9e9a-029f4fd9f35f
Journal backup:           inode blocks
Journal features:         journal_incompat_revoke
Journal size:             128M
Journal length:           32768
Journal sequence:         0x00257963
Journal start:            31445

```

It looks like my partition has a higher number of inodes per group and inode blocks per group than yours does (about twice as many).

You should be able to write to the disk because you have free inodes, so I dunno what the deal is.

---

### Post by gregom on 2013-06-14
I think I ran that command after letting the system sit for awhile and the zoneminder service cleaned up old files. Later when I checked it, the free inodes was 0. 

I went ahead and reformatted my volume with 16384 bytes per inode. That changed my indodes per group to 8192 and inode blocks per group to 512. 

Now that i've been running a full 24 hours recording video, things are looking better (but not perfect). I have 3% disk space used and 4% of my inodes used. So I will still run out of inodes before I run out of disk space.

I may need to start a new thread on this now that I have a better understanding, but I still need help from someone who understands it and my situation. I don't know enough to decide if formatting with 8192 bytes per inode will have any negative effects on my configuration.

---

### Post by CharlesA on 2013-06-14
Mine are currently at 8192.

```
charles@Thor:~$ sudo tune2fs /dev/sdb1 -l | grep Inode
Inode count:              183148544
Inodes per group:         8192
Inode blocks per group:   512
Inode size:               256

```
[http://stackoverflow.com/questions/3618820/how-many-bytes-per-inodes](http://stackoverflow.com/questions/3618820/how-many-bytes-per-inodes)

So far no issues, but I'm only using 1% of my inodes:

```
charles@Thor:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdc1       3.6T  3.3T  342G  91% /array
charles@Thor:~$ df -hi
Filesystem     Inodes IUsed IFree IUse% Mounted on
/dev/sdc1        233M  972K  232M    1% /array

```

---

### Post by carboi82 on 2013-06-14
Ive grown a raid5 array quite a few times, and have seen this between the steps of creating the array and expanding the file system to use all of it (some systems read size based on the physical drives, and others read size based on the file system on it).  Have you by chance grown the array by adding hdds to it?

---

### Post by gregom on 2013-06-17
Well it probably depends on what kinds of files you have on your array. I have millions of 8 KB and 14 KB files.

I am now at 9% disk space used, and 10% inodes used. So a lot better than before...

---

