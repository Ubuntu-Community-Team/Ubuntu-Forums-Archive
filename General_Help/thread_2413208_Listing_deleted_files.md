---
title: "Listing deleted files?"
date: 2019-02-22
forum: General Help
---

### Post by asearle on 2019-02-22
Hallo Everyone,

I will be passing a laptop on to a friend and before I do so, I wanted to quickly check what deleted material I have on the disk: There are a couple of files which I would like to retrieve and want to double-check that they are not on that disk.

Anyway, there seems to be a whole lot of "undelete" software/tools available and I am quite confused about which one I should try. And many of them seem intended to work with external disks and sticks rather than the current (mounted) drive.

Can anyone point me in the right direction for this particular task? Any tips that you can give me would be a great help.

Many thanks,
Alan (in Cologne)

PS: I use Lubuntu but can log in to the Ubuntu desktop too if need be.

---

### Post by #&amp;thj^% on 2019-02-22
This is quite an undertaking, but see if this helps: [https://unix.stackexchange.com/questions/292510/view-list-of-deleted-files](https://unix.stackexchange.com/questions/292510/view-list-of-deleted-files)
```
sudo debugfs /dev/sda4
[sudo] password for me: 
debugfs 1.44.5 (15-Dec-2018)
debugfs:  lsdel
 Inode  Owner  Mode    Size      Blocks   Time deleted
0 deleted inodes found.
```
EDIT: I forgot to mention how to exit debugfs, Simply hit the {q or Q} key

---

### Post by asearle on 2019-02-23
Many thanks for this tip: It sounds like a good option.

However I ran the command and got the result "0 deleted inodes found" so I assumed that there were no deleted files available to recover. Then I deleted a couple of files expecting to see them appear but I still got the "0 deleted inodes found" message.

Am I doing something wrong here?

Many thanks,
Alan

---

### Post by asearle on 2019-03-04
Can anyone out there give me another tip on this topic: I have been experimenting with the command above (including specifically creating and deleting files) but always get "0 deleted inodes found".

Or can anyone suggest alternative syntax to list deleted files?

Many thanks,
Alan

---

### Post by Impavidus on 2019-03-04
I'm not entirely sure what you try to do. Are you trying to recover some lost files? In that case I can do little more than provide this link: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Data recovery tools may be able to find (pieces of) deleted files.

Or do you want to make sure that the files are really gone, so that you friend cannot recover those files, even if he tries really hard? In that case, the easiest option is to wipe the drive completely, then make a fresh install of the operating system. Boot a live disk, overwrite the hard drive with zeros and install. Or leave installing to your friend, maybe he wants to do it himself.

---

### Post by asearle on 2019-03-04
Many thanks for the tips.

Just to clarify my goal ...

I simply want a listing of deleted files to see whether I want/need to recover them. The "debugfs" command looks like it is exactly what I need ... but it doesn't produce a listing. I must be doing something wrong.

Thanks for any tips.

---

### Post by #&amp;thj^% on 2019-03-04
> **asearle said:**
> Many thanks for the tips.

Just to clarify my goal ...

I simply want a listing of deleted files to see whether I want/need to recover them. The "debugfs" command looks like it is exactly what I need ... but it doesn't produce a listing. I must be doing something wrong.

Thanks for any tips.

What i first showed is a safe example, not a way to find deleted files.
To use you will need to login as root (Beware and careful here).
Now when your in #ROOT use:
```
# debugfs
```
Now you will want to open the file system via:

```
debugfs:  [COLOR="#FF0000"]open /dev/sda4[/COLOR]
```
NOTE the only command you will add there is "open /dev/sda4" or the path for your device.>>(Just for clarity)
Now we check for all the shown inodes with:
Example for mine:
```
debugfs:  [COLOR="#FF0000"]lsdel[/COLOR]
 Inode  Owner  Mode    Size      Blocks   Time deleted
143123   1000 100644  52891     13/    13 Fri Jan  2 08:42:50 1970
1 deleted inodes found.
debugfs:  

```
Please be aware that you can cause great damage with the wrong commands with this nifty tool.
Examples can found here also: [https://geek-university.com/linux/debug-a-file-system/](https://geek-university.com/linux/debug-a-file-system/)
And a bit more complete: [https://www.systutorials.com/docs/linux/man/8-debugfs/](https://www.systutorials.com/docs/linux/man/8-debugfs/)
And just to see stats:
```
debugfs:  stats
Filesystem volume name:   <none>
Last mounted on:          /
Filesystem UUID:          5f99a7eb-5b70-4c03-a242-6e6eb06ca208
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype n
eeds_recovery extent 64bit flex_bg sparse_super large_file huge_file dir_nlink e
xtra_isize metadata_csum
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              10452992
Block count:              41809920
Reserved block count:     1930337
Free blocks:              35364931
Free inodes:              9886557
First block:              0
Block size:               4096
Fragment size:            4096
Group descriptor size:    64
Reserved GDT blocks:      1017
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Mon Dec 10 06:37:30 2018
Last mount time:          Mon Mar  4 06:32:29 2019
Last write time:          Mon Mar  4 06:32:29 2019
Mount count:              165
Maximum mount count:      -1
Last checked:             Mon Dec 10 06:55:13 2018
Check interval:           0 (<none>)
Lifetime writes:          641 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     32
Desired extra isize:      32
Journal inode:            8
First orphan inode:       143027
Default directory hash:   half_md4
Directory Hash Seed:      7bf3d53b-f7dd-4393-bc42-5f41fc1df99e
Journal backup:           inode blocks
Checksum type:            crc32c
Checksum:                 0x67c57375
Directories:              43176
 Group  0: block bitmap at 1045, inode bitmap at 1061, inode table at 1077
           23484 free blocks, 8159 free inodes, 14 used directories, 8000 unused
 inodes
           [Checksum 0x4c56]
 Group  1: block bitmap at 1046, inode bitmap at 1062, inode table at 1589
           1766 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0xf675]
 Group  2: block bitmap at 1047, inode bitmap at 1063, inode table at 2101
           2524 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0xe824]
 Group  3: block bitmap at 1048, inode bitmap at 1064, inode table at 2613
           1192 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0x4885]
 Group  4: block bitmap at 1049, inode bitmap at 1065, inode table at 3125
           1917 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0x07c5]
 Group  5: block bitmap at 1050, inode bitmap at 1066, inode table at 3637
           3065 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0x5df0]
 Group  6: block bitmap at 1051, inode bitmap at 1067, inode table at 4149
           2886 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0xcee8]
 Group  7: block bitmap at 1052, inode bitmap at 1068, inode table at 4661
           2459 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0xf2cc]
 Group  8: block bitmap at 1053, inode bitmap at 1069, inode table at 5173
           1384 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0x7892]
 Group  9: block bitmap at 1054, inode bitmap at 1070, inode table at 5685
           1293 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0x0d3b]
 Group 10: block bitmap at 1055, inode bitmap at 1071, inode table at 6197
           2237 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0xcc32]
 Group 11: block bitmap at 1056, inode bitmap at 1072, inode table at 6709
           1364 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0xdafd]
 Group 12: block bitmap at 1057, inode bitmap at 1073, inode table at 7221
           245 free blocks, 8192 free inodes, 0 used directories, 8192 unused in
odes
           [Inode not init, Checksum 0xa90a]
 Group 13: block bitmap at 1058, inode bitmap at 1074, inode table at 7733
           10891 free blocks, 8192 free inodes, 0 used directories, 8192 unused 
inodes
           [Inode not init, Checksum 0x09ef]
 Group 14: block bitmap at 1059, inode bitmap at 1075, inode table at 8245
           2210 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0x9510]
 Group 15: block bitmap at 1060, inode bitmap at 1076, inode table at 8757
           12898 free blocks, 8192 free inodes, 0 used directories, 8192 unused 
inodes
           [Inode not init, Checksum 0x3be7]
 Group 16: block bitmap at 524288, inode bitmap at 524304, inode table at 524320
           22904 free blocks, 0 free inodes, 379 used directories, 0 unused inod
es
           [Checksum 0x9384]
 Group 17: block bitmap at 524289, inode bitmap at 524305, inode table at 524832
           3316 free blocks, 4327 free inodes, 0 used directories, 3818 unused i
nodes
           [Checksum 0x2d73]
 Group 18: block bitmap at 524290, inode bitmap at 524306, inode table at 525344
           18063 free blocks, 8192 free inodes, 0 used directories, 8192 unused 
inodes
           [Inode not init, Checksum 0xc510]
 Group 19: block bitmap at 524291, inode bitmap at 524307, inode table at 525856
           9767 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0x6e88]
 Group 20: block bitmap at 524292, inode bitmap at 524308, inode table at 526368
           15674 free blocks, 8192 free inodes, 0 used directories, 8192 unused 
inodes
           [Inode not init, Checksum 0x543e]
 Group 21: block bitmap at 524293, inode bitmap at 524309, inode table at 526880
           5309 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0x67f5]
 Group 22: block bitmap at 524294, inode bitmap at 524310, inode table at 527392
           5890 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0x22d4]
 Group 23: block bitmap at 524295, inode bitmap at 524311, inode table at 527904
           7938 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0x3413]
 Group 24: block bitmap at 524296, inode bitmap at 524312, inode table at 528416
           4167 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0xb08a]
 Group 25: block bitmap at 524297, inode bitmap at 524313, inode table at 528928
           1829 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0xa2a6]
 Group 26: block bitmap at 524298, inode bitmap at 524314, inode table at 529440
           26742 free blocks, 8192 free inodes, 0 used directories, 8192 unused 
inodes
           [Inode not init, Checksum 0x4ced]
 Group 27: block bitmap at 524299, inode bitmap at 524315, inode table at 529952
           16385 free blocks, 8192 free inodes, 0 used directories, 8192 unused 
inodes
           [Inode not init, Checksum 0xe1e2]
 Group 28: block bitmap at 524300, inode bitmap at 524316, inode table at 530464
           16285 free blocks, 8192 free inodes, 0 used directories, 8192 unused 
inodes
           [Inode not init, Checksum 0x3e77]
 Group 29: block bitmap at 524301, inode bitmap at 524317, inode table at 530976
           17048 free blocks, 8192 free inodes, 0 used directories, 8192 unused 
inodes
           [Inode not init, Checksum 0xcc6a]
 Group 30: block bitmap at 524302, inode bitmap at 524318, inode table at 531488
           8424 free blocks, 8192 free inodes, 0 used directories, 8192 unused i
nodes
           [Inode not init, Checksum 0x3c0f]
 Group 31: block bitmap at 524303, inode bitmap at 524319, inode table at 532000
           11600 free blocks, 8192 free inodes, 0 used directories, 8192 unused 
inodes
           [Inode not init, Checksum 0xfe56]
 Group 32: block bitmap at 1048576, inode bitmap at 1048592, inode table at 1048
608
           18169 free blocks, 3872 free inodes, 212 used directories, 1284 unuse
d inodes
           [Checksum 0x6505]
 Group 33: block bitmap at 1048577, inode bitmap at 1048593, inode table at 1049
120
           219 free blocks, 8192 free inodes, 0 used directories, 8192 unused in
odes
           [Inode not init, Checksum 0xc9de]
 Group 34: block bitmap at 1048578, inode bitmap at 1048594, inode table at 1049
632

```
I'm sure this is not as easy as you had first thought or even hoped, as I first warned with **"This is quite an undertaking"**

---

