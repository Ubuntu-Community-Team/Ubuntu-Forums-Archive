---
title: "Unable to mount location Newb help please"
date: 2015-09-21
forum: General Help
---

### Post by meXimo on 2015-09-21
Hello i am new to this community and id like to know more about this .
I explain my problem i installed Linux on an other hard drive and it still contains some Datas that were not backup ed
I am pretty sure that i could still mount it again because earlier this day i succeeded at it unfortunately i can not mount it anymore i had a look at it on the internet but as you know people don't often post about the way they succeded  .
 i have error from the windows 


""Error mounting /dev/sdc1 at /media/user/local: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdc1" "/media/user/local"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so""
[COLOR=#8b4513]
[/COLOR][COLOR=#ff0000]and a warning from gparted [/COLOR]

<i>Filesystem volume name:   local
Last mounted on:          /media/user/90d1aabf-fabb-484c-ac50-f8075a45dfcc
Filesystem UUID:          90d1aabf-fabb-484c-ac50-f8075a45dfcc
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              60801024
Block count:              243176704
Reserved block count:     12158835
Free blocks:              51484041
Free inodes:              60370830
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      966
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sat Sep  5 18:57:29 2015
Last mount time:          Mon Sep 21 19:42:33 2015
Last write time:          Mon Sep 21 22:16:31 2015
Mount count:              74
Maximum mount count:      -1
Last checked:             Sat Sep  5 18:57:29 2015
Check interval:           0 (<none>)
Lifetime writes:          754 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
[COLOR=#ff0000]
  dmesg | tail[/COLOR]
[ 1477.210736]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1477.210740]         00 00 29 08 
[ 1477.210742] sd 7:0:0:0: [sdc]  
[ 1477.210743] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1477.210744] sd 7:0:0:0: [sdc] CDB: 
[ 1477.210745] Read(10): 28 00 00 00 29 08 00 00 08 00
[ 1477.210749] end_request: I/O error, dev sdc, sector 10504
[ 1477.210759] ata8: EH complete
[ 1477.210786] EXT4-fs error (device sdc1): __ext4_get_inode_loc:3932: inode #8: block 1057: comm mount: unable to read itable block
[ 1477.214387] EXT4-fs (sdc1): no journal found


[COLOR=#ff0000]sudo blkid -c /dev/null[/COLOR]
/dev/sda1: UUID="db6f4190-c9c8-4ded-9adb-6cd32108c290" TYPE="ext4" 
/dev/sdb1: LABEL="files1" UUID="30fb852b-4d72-45ab-b06e-3bfbb769c479" TYPE="ext4" 
/dev/sdc1: LABEL="local" UUID="90d1aabf-fabb-484c-ac50-f8075a45dfcc" TYPE="ext4"

I guess this is a sector error but i didn't found no way to fix this .
I also think that a computer forensics would laugh at me but i am not so please be forgiving to me .
Any help from you wouldn't be extra please help me thanks for reading and you patience

---

### Post by nknwn on 2015-09-21
**Check and Repair Your Filesystem With fsck**

[https://www.maketecheasier.com/check-repair-filesystem-fsck-linux/](https://www.maketecheasier.com/check-repair-filesystem-fsck-linux/)

---

### Post by meXimo on 2015-09-22
Thanks for the help i still got issues   terminal shows me this        ```
   user@user-MS-7760 ~/Desktop $ sudo fsck -a /dev/sdc1    fsck from util-linux 2.20.1  fsck.ext4: Bad magic number in super-block while trying to open /dev/sdc1 /dev/sdc1:  The superblock could not be read or does not describe a valid ext2/ext3/ext4 filesystem.       If the device is valid and it really contains an ext2/ext3/ext4 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:     e2fsck -b 8193   or     e2fsck -b 32768    
```    as    the computer offers me to i try       so   ```
user@user-MS-7760 ~ $   sudo  e2fsck -b 8193 /dev/sdc1     e2fsck 1.42.9 (4-Feb-2014) e2fsck: Bad magic number in super-block while trying to open /dev/sdc1  The superblock could not be read or does not describe a valid ext2/ext3/ext4 filesystem.  If the device is valid and it really contains an ext2/ext3/ext4 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:     e2fsck -b 8193   or     e2fsck -b 32768         user@user-   
``` ```
MS-7760 ~ $ sudo e2fsck -b 32768 /dev/sdc1        e2fsck 1.42.9 (4-Feb-2014) e2fsck: Bad magic number in super-block while trying to open /dev/sdc1  The superblock could not be read or does not describe a valid ext2/ext3/ext4 filesystem   If the device is valid and it really contains an ext2/ext3/ext4 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:     e2fsck -b 8193   or     e2fsck -b 32768       
```   also trying testdisk as well    TestDisk 6.14, Data Recovery Utility, July 2013 Christophe GRENIER  [http://www.cgsecurity.org](http://www.cgsecurity.org)  Disk /dev/sdc - 1000 GB / 931 GiB - CHS 121601 255 63       Partition                  Start        End    Size in sectors > 1 P Linux                    0  32 33 121096 133 61 1945413632   Search ext2/ext3/ext4 superblock   21233664/1945413632 1%  and then it stops   But it does not seem to find the superblock   :(

---

### Post by Bucky Ball on 2015-09-22
*Thread moved to **General Help**.*

@meXimo: Welcome. Please see the last link in my signature for how to use code tags for output. Your last post is pretty well unreadable and does little for your chances of support. Thanks.

Boot from the Ubuntu install media, DVD or USB, 'Try Ubuntu', see what you see there and if you can mount the partition by clicking on it. If not, then mount it manually by opening a terminal and:

```
sudo mkdir /media/sdc1
sudo mount /dev/sdc1 /media/sdc1
```

Does it mount? If so, back up valuable data to an external device and start again. 

I'm not too sure what's happened here but looks very messy. In future, backup all valuable data and leave free space to install Ubuntu into. Unsure as to how you went about this install, but we all live and learn ... :-k

PS: I see you've tried to clean up your last post. Code tags, please. It will keep the formatting of the terminal output and you won't need to mess about with it. Just copy/paste/add tags. :)

---

### Post by nknwn on 2015-09-22
What I would do next is run photorec [http://www.cgsecurity.org/](http://www.cgsecurity.org/) to try to recover the files then format the bad partition clean.
**PhotoRec Step By Step:**
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by Bucky Ball on 2015-09-22
> **nknwn said:**
> What I would do next is run photorec [http://www.cgsecurity.org/](http://www.cgsecurity.org/) to try to recover the files then format the bad partition clean.
**PhotoRec Step By Step:**
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Your getting ahead of yourself. There is no response from the OP about what I have suggested. Any data might be easily retrievable using a Live session. No need for photorec ... yet. :)

Let's perhaps wait before heading down the garden path and throwing a heap of, possibly unrequired, suggestions into the ring ...

---

### Post by nknwn on 2015-09-22
> **Bucky Ball said:**
> Your getting ahead of yourself. There is no response from the OP about what I have suggested. Any data might be easily retrievable using a Live session. No need for photorec ... yet. :)

Let's perhaps wait before heading down the garden path and throwing a heap of, possibly unrequired, suggestions into the ring ...

Of course I Agree  ..  I hadn't read your reply when I posted mine. It hadn't appeared when I started composing and collecting links :D

---

### Post by Bucky Ball on 2015-09-22
I'm still fairly confused as to what's actually happened here so being careful not to add to the dog's breakfast we are already faced with. :D

---

### Post by meXimo on 2015-09-25
```
user-MS-7760 Desktop # cd /  user-MS-7760 / # sudo mkdir /media/sdc1 user-MS-7760 / # sudo mount /dev/sdc1 /media/sdc3  
```   Nope sir this does not work my computer seems to be waiting for something and the process is still pending since yesterday .

---

### Post by Bucky Ball on 2015-09-25
If this:

```
cd /  user-MS-7760 / # sudo mkdir /media/sdc1 user-MS-7760 / # sudo mount /dev/sdc1 /media/sdc3
```

... is what you typed in a terminal, no, it wouldn't work. There are two commands, exactly as it is typed in post #4. :)

---

