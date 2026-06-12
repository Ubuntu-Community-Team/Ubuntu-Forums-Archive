---
title: "Repair corrupt filesystem using fsck on CF"
date: 2019-09-20
forum: General Help
---

### Post by mockforce on 2019-09-20
Hey All,

Not new to linux, but I'm new to repairing a filesystem. I've read using fsck for file system repair is fairly simple but I'm finding it not be working as easy as I expect

This is what the system looks like before I attempt to fix. I made an image to return the system to the same state of disrepair it started as.

this is from ```
ls -li
``` on the corrupt partition

```

total 124
 8132 -rw-r--r--  1 root            root     1586 Oct  6  2009 bin
 2899 -rw-------  1 sarnold         sarnold  3761 Feb 24  2016 boot
   14 lrwxrwxrwx  1 root            root       11 Feb 16  2010 cdrom -> media/cdrom
    ? d?????????  ? ?               ?           ?            ? dev
    ? d?????????  ? ?               ?           ?            ? etc
    ? d?????????  ? ?               ?           ?            ? home
20542 lrwxrwxrwx  1 root            root       37 Feb 16  2010 initrd.img -> boot/initrd.img-2.6.31-19-generic-pae
 8131 -rw-r--r--  1 root            root     4684 Feb 16  2010 lib
   11 drwx------ 28 root            root    16384 Mar 21  2010 lost+found
24385 drwxr-xr-x  7 root            root     4096 Apr 28  2011 media
    ? d?????????  ? ?               ?           ?            ? mnt
 8157 drwxr-xr-x  2 root            root     4096 Feb 16  2010 opt
    ? d?????????  ? ?               ?           ?            ? proc
    ? l?????????  ? ?               ?           ?            ? name
25004 drwxr-xr-x  2 sarnold         sarnold  4096 Sep 23  2010 name-bak
    ? d?????????  ? ?               ?           ?            ? root
    ? d?????????  ? ?               ?           ?            ? sbin
 8133 -rw-r--r--  1 root            root     4916 Feb 16  2010 selinux
 8156 drwxr-xr-x  2 root            root     4096 Feb 16  2010 srv
 8137 -rwxr-xr-x  1 root            root     1503 Sep 21  2009 sys
    ? d?????????  ? ?               ?           ?            ? tmp
    ? d?????????  ? ?               ?           ?            ? usr
 8129 -rw-r-----  1 systemd-resolve adm     64693 Jun 24  2018 var
20543 lrwxrwxrwx  1 root            root       34 Feb 16  2010 vmlinuz -> boot/vmlinuz-2.6.31-19-generic-pae



```


this is from the unmounted system and running the following

```

sudo fsck -y /dev/sdb1


fsck from util-linux 2.31.1
/dev/sdb1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inode 8 extent tree (at level 2) could be narrower.  Fix? yes


Deleted inode 17 has zero dtime.  Fix? yes


Deleted inode 273 has zero dtime.  Fix? yes


Deleted inode 274 has zero dtime.  Fix? yes


Deleted inode 276 has zero dtime.  Fix? yes


Deleted inode 278 has zero dtime.  Fix? yes


Deleted inode 280 has zero dtime.  Fix? yes


Deleted inode 282 has zero dtime.  Fix? yes


Deleted inode 284 has zero dtime.  Fix? yes


Deleted inode 286 has zero dtime.  Fix? yes


Inode 289 is in use, but has dtime set.  Fix? yes


Inode 289 has imagic flag set.  Clear? yes


Inodes that were part of a corrupted orphan linked list found.  Fix? yes


Inode 290 was part of the orphaned inode list.  FIXED.
Inode 291 was part of the orphaned inode list.  FIXED.
Inode 291 seems to have inline data but extent flag is set.
Fix? yes


Inode 291 has INLINE_DATA_FL flag on filesystem without inline data support.
Clear? yes


Inode 292 is in use, but has dtime set.  Fix? yes


Inode 292 has imagic flag set.  Clear? yes


Inode 292 has a extra size (19001) which is invalid
Fix? yes


Inode 293 is in use, but has dtime set.  Fix? yes


Inode 293 has a extra size (26723) which is invalid
Fix? yes


Inode 293 has a bad extended attribute block 39246.  Clear? yes


Inode 293, i_size is 74309464574226020, should be 0.  Fix? yes


Inode 293, i_blocks is 121380070789240, should be 0.  Fix? yes


Inode 294 was part of the orphaned inode list.  FIXED.
Inode 294 has imagic flag set.  Clear? yes


Inode 294 has a extra size (30316) which is invalid
Fix? yes


Inode 295 was part of the orphaned inode list.  FIXED.
Inode 295 has a extra size (27749) which is invalid
Fix? yes


Inode 296 is in use, but has dtime set.  Fix? yes


Inode 296 has imagic flag set.  Clear? yes


Inode 296 has a extra size (28205) which is invalid
Fix? yes


Inode 297 is in use, but has dtime set.  Fix? yes


Inode 297 has imagic flag set.  Clear? yes


Inode 297 has a extra size (119) which is invalid
Fix? yes


Inode 298 was part of the orphaned inode list.  FIXED.
Inode 298 has imagic flag set.  Clear? yes


Inode 298 has a extra size (29804) which is invalid
Fix? yes


Inode 298, i_size is 6878245050991666539, should be 0.  Fix? yes


Inode 298, i_blocks is 121377528176994, should be 0.  Fix? yes


Inode 299 is in use, but has dtime set.  Fix? yes


Inode 299 has imagic flag set.  Clear? yes


Inode 299 has a extra size (44916) which is invalid
Fix? yes


Inode 300 is in use, but has dtime set.  Fix? yes


Inode 300 has imagic flag set.  Clear? yes


Inode 301 was part of the orphaned inode list.  FIXED.
Inode 301 has imagic flag set.  Clear? yes


Inode 301 has INDEX_FL flag set but is not a directory.
Clear HTree index? yes


Inode 301, i_size is 3348267310409973780, should be 0.  Fix? yes


Inode 301, i_blocks is 53443000685, should be 0.  Fix? yes


Inode 303 has INLINE_DATA_FL flag on filesystem without inline data support.
Clear? yes


Inode 411, end of extent exceeds allowed value
    (logical block 3, physical block 557411, len 10)
Clear? yes


Inode 411, end of extent exceeds allowed value
    (logical block 14, physical block 557422, len 18)
Clear? yes


Inode 411, end of extent exceeds allowed value
    (logical block 33, physical block 557441, len 25)
Clear? yes


Inode 411, end of extent exceeds allowed value
    (logical block 59, physical block 557467, len 10)
Clear? yes


Inode 411, end of extent exceeds allowed value
    (logical block 70, physical block 557478, len 11)
Clear? yes


Inode 411, end of extent exceeds allowed value
    (logical block 82, physical block 557490, len 16)
Clear? yes


Inode 411, i_blocks is 48, should be 32.  Fix? yes

... (bunch more stuff)

Free inodes count wrong for group #5 (4860, counted=4868).
Fix? yes


Directories count wrong for group #5 (339, counted=280).
Fix? yes


Free inodes count wrong for group #6 (7374, counted=6577).
Fix? yes


Directories count wrong for group #6 (144, counted=934).
Fix? yes


Free inodes count wrong for group #7 (7222, counted=7238).
Fix? yes


Directories count wrong for group #7 (90, counted=74).
Fix? yes


Directories count wrong for group #8 (611, counted=595).
Fix? yes


Directories count wrong for group #9 (430, counted=418).
Fix? yes


Free inodes count wrong for group #10 (7934, counted=7943).
Fix? yes


Directories count wrong for group #10 (67, counted=51).
Fix? yes


Directories count wrong for group #11 (28, counted=14).
Fix? yes


Free inodes count wrong (124458, counted=123605).
Fix? yes




/dev/sdb1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sdb1: 38955/162560 files (1.3% non-contiguous), 372712/640000 blocks


```

This is the filesystem after the fsck -y /dev/sdb1. The same thing happens when I try to repair the superblock command fsck -y -f -b /dev/sdb1 #####(the location of the next superblock)

```

ls -li /media/user/b4e5ced2-6204-4185-b684-d92ca05052f1/
total 148
 8132 -rw-r--r--   1 root            root     1586 Oct  6  2009 bin
 2899 -rw-------   1 sarnold         sarnold  3761 Feb 24  2016 boot
   14 lrwxrwxrwx   1 root            root       11 Feb 16  2010 cdrom -> media/cdrom
20542 lrwxrwxrwx   1 root            root       37 Feb 16  2010 initrd.img -> boot/initrd.img-2.6.31-19-generic-pae
 8131 -rw-r--r--   1 root            root     4684 Feb 16  2010 lib
   11 drwx------ 216 root            root    40960 Mar 21  2010 lost+found
24385 drwxr-xr-x   7 root            root     4096 Apr 28  2011 media
 8157 drwxr-xr-x   2 root            root     4096 Feb 16  2010 opt
25004 drwxr-xr-x   2 sarnold         sarnold  4096 Sep 23  2010 name-bak
 8133 -rw-r--r--   1 root            root     4916 Feb 16  2010 selinux
 8156 drwxr-xr-x   2 root            root     4096 Feb 16  2010 srv
 8137 -rwxr-xr-x   1 root            root     1503 Sep 21  2009 sys
 8129 -rw-r-----   1 systemd-resolve adm     64693 Jun 24  2018 var
20543 lrwxrwxrwx   1 root            root       34 Feb 16  2010 vmlinuz -> boot/vmlinuz-2.6.31-19-generic-pae



```

So I'm at a loss as to how to proceed. The files core to the system appear to have no inode number and I'm not finding many good resources to better understand what fsck is actually attempting to do to recover the system so the inode yes/no's are a bit of a mystery to me.

let me know, if more information about the system. I'll add more details in replies as I try different stuff. I think I'm going to try gparted next.

Lastly here's the top of the dumpe2fs of the corrupt filesystem

```

Filesystem volume name:   <none>
Last mounted on:          /media/sarnold/mnt1
Filesystem UUID:          b4e5ced2-6204-4185-b684-d92ca05052f1
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         not clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              162560
Block count:              640000
Reserved block count:     31998
Free blocks:              328613
Free inodes:              124390
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      912
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8128
Inode blocks per group:   508
RAID stride:              32622
Flex block group size:    16
Filesystem created:       Tue Feb 16 13:43:49 2010
Last mount time:          Fri Sep 20 15:18:32 2019
Last write time:          Fri Sep 20 15:18:32 2019
Mount count:              8
Maximum mount count:      23
Last checked:             Wed May  4 19:31:35 2011
Check interval:           15552000 (6 months)
Next check after:         Mon Oct 31 19:31:35 2011
Lifetime writes:          109 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      cd5139fb-4096-46ec-8f26-a1dd5798f922
Journal backup:           inode blocks
FS Error count:           368
First error time:         Mon Sep  9 11:02:45 2019
First error function:     ext4_lookup
First error line #:       1581
First error inode #:      2
First error block #:      0
Last error time:          Fri Sep 20 15:18:32 2019
Last error function:      ext4_lookup
Last error line #:        1581
Last error inode #:       2
Last error block #:       0
Journal features:         journal_incompat_revoke
Journal size:             128M
Journal length:           32768
Journal sequence:         0x009552c5
Journal start:            1




Group 0: (Blocks 0-32767) csum 0x2c98 [ITABLE_ZEROED]
  Primary superblock at 0, Group descriptors at 1-1
  Reserved GDT blocks at 2-913
  Block bitmap at 914 (+914)
  Inode bitmap at 930 (+930)
  Inode table at 946-1453 (+946)
  5772 free blocks, 7 free inodes, 159 directories

```

---

### Post by TheFu on 2019-09-20
I would run **smartctl** tests and reports on the disk, then decide if just wiping the disk and restoring from backups was an option or if I needed a new HDD instead.  The SMART data would massively control what I did.

It appears that the root directory had issues.  I've never seen that.

```
 2899 -rw-------   1 sarnold         sarnold  3761 Feb 24  2016 boot
```
looks wrong.  /boot should be a directory, something like this:
```
$ ll -d /boot
drwxr-xr-x 5 root root 4096 Sep 14 12:39 /boot/
```

If I'm asked to fix more than 2 things under an fsck, I'd break out and use the -y switch to automatically fix everything. It isn't like there is a choice.  Anything really bad either gets restored from backups or a new disk is swapped in and backups restored to it.  I can do all the data recovery/testing/thinking on the old disk later, after the issue is handled and the machine it back online.

Discovered this morning that a boot disk on a box has over 10 relocated sectors.  During maintenance this weekend, it will be swapped out for a comparable disk. I'll try to force those sectors to be restored using some tools, but it will never be trusted for an OS again.  Basically, it will be used for sneaker-net stuff going forward.

BTW, to be most helpful, it is nice to show the exact command with all options used for the output.  And big thanks for using code tags. This all helps the less informed in the community be able to do the same if they have a similar issue.

---

### Post by mockforce on 2019-09-23
Thanks for the input, unfortunately this OS version doesn't have a known back-up which is actually why I'm trying to recover what I can. I have backups of the system as I received it unfortunately my predecessor left the hardware in disarray.

Regarding the smartctl, I'm going to give that a try, I've never used it before. After the installation I was able to get the following from the mounted device.

```

sudo smartctl -a /dev/sdb1
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-5.0.0-29-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Vendor:               Generic-
Product:              Multi-Card
Revision:             1.00
Compliance:           SPC-4
User Capacity:        8,153,284,608 bytes [8.15 GB]
Logical block size:   512 bytes
Logical Unit id:      0x00e04c2020202000error: designator length
Serial number:        2012090114345300
Device type:          disk
Local Time is:        Mon Sep 23 08:32:59 2019 EDT
SMART support is:     Available - device has SMART capability.
SMART support is:     Enabled
Temperature Warning:  Disabled or Not Supported


=== START OF READ SMART DATA SECTION ===
SMART Health Status: OK
Current Drive Temperature:     0 C
Drive Trip Temperature:        0 C


Error Counter logging not supported


Device does not support Self Test logging



```

---

### Post by TheFu on 2019-09-23
smartctl has many options which are documented in the manpage.
It is normal to run a test before asking for test results.  There are multiple types of testing available.  I generally do a long test every week and a short test is something comes up mid-week.

BTW, tests specifying a partition aren't needed.  The entire disk is tested.  If the desire is to test multiple, similar disks, smartctl accepts normal bash globbing, according to the manpage: "/dev/sd[a-z]".  Of course, different controllers might require different options, so testing groups of disks might be needed.

UPDATE: I didn't remember this was a CF.  Make a bit-for-bit clone ASAP and do anything else using that cloned storage.  The clone can go to any sort of storage.  After all, in Unix, "everything is a file".  Then you can mount the new image using a loop device and treat it like a HDD, CF, partition, whatever.  It isn't hard, just multiple steps that are reasonably documented.  **kpartx** is handy for finding the start of partitions inside an image file.

---

### Post by mockforce on 2019-09-23
[https://unix.stackexchange.com/questions/115082/understanding-smartctl-output-for-a-cf-card](https://unix.stackexchange.com/questions/115082/understanding-smartctl-output-for-a-cf-card) 

This article makes me feel that smartctl may not be the best option for a CF like the one I'm using.

---

### Post by TheFu on 2019-09-23
> **mockforce said:**
> [https://unix.stackexchange.com/questions/115082/understanding-smartctl-output-for-a-cf-card](https://unix.stackexchange.com/questions/115082/understanding-smartctl-output-for-a-cf-card) 

This article makes me feel that smartctl may not be the best option for a CF like the one I'm using.

Sorry - I didn't remember the CF part.  You may be stuck. Hopefully, you made a **ddrescue** copy before doing anything else.  Flash media wears out in different ways.  Parts become unreadable, then disappear, if you are lucky.  Sometimes flash stops working completely.

Time to have the bosses open the wallet to get a replacement for the OS. I'm assuming this isn't ubuntu and is some sort of embedded device.

I updated the post earlier today - **kpartx** - after the clone is made, will be useful.

---

