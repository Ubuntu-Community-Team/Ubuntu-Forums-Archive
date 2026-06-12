---
title: "Can;t get fsck to run on boot on non-OS disks"
date: 2015-02-13
forum: General Help
---

### Post by brickbat on 2015-02-13
Hi, I'm running ubuntu 14.04.  When I do 

```


sudo tune2fs -l /dev/sdq1 shows

Filesystem volume name:   Downloads1Lin
Last mounted on:          /media/server/Downloads1Lin
Filesystem UUID:          9fd96190-80c0-46c9-ba7b-797ec9cea5ed
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              244195328
Block count:              976754176
Reserved block count:     48837708
Free blocks:              164951839
Free inodes:              244175431
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      791
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Mon Jul 14 16:27:59 2014
Last mount time:          Sat Feb 14 01:55:16 2015
Last write time:          Sat Feb 14 01:55:16 2015
Mount count:              163
Maximum mount count:      1
Last checked:             Mon Jul 14 16:27:59 2014
Check interval:           86400 (1 day)
Next check after:         Tue Jul 15 16:27:59 2014
Lifetime writes:          15 TB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      636cb592-d4cb-4e97-bace-b333aca119de
Journal backup:           inode blocks

```

It doesnt make any sense to me.

I have a lot of disks connected to this system and it looks like none of them are being checked.

When I try 

sudo touch /forcefsck

it only checks the system partition.

Would appreciate it if someone can help me set it up so it actually checks all the disks mounted in fstab on boot every week

Thanks
bb

---

