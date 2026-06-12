---
title: "fsck is not running on 18.04, even with tun2fs mount count set to 1"
date: 2018-10-10
forum: General Help
---

### Post by dman7773 on 2018-10-10
[COLOR=#242729][FONT=Arial]fsck is not running on my root drive on Ubuntu 18.04 LTS server edition[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have tried fsck.mode=force in grub on the kernel command line to no success.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have set the mount count to 1 with tune2fs -c 1 /dev/sda2 and rebooted and still no fsck. Instead I just get a text message saying you need to do a fsck on /dev/sda2.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any ideas on what is going on?

```
[FONT=Consolas]one@localhost:~$ sudo tune2fs -l /dev/sda2 [/FONT][/FONT][/COLOR]
tune2fs 1.44.1 (24-Mar-2018)
Filesystem volume name:   <none>
Last mounted on:          /
Filesystem UUID:          36589912-c6ab-11e8-93a6-7085c27cfaec
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent 64bit flex_bg sparse_super large_file huge_file dir_nlink extra_isize metadata_csum
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              6160384
Block count:              24641536
Reserved block count:     1232076
Free blocks:              19441110
Free inodes:              5417720
First block:              0
Block size:               4096
Fragment size:            4096
Group descriptor size:    64
Reserved GDT blocks:      1024
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Tue Oct  2 20:25:28 2018
Last mount time:          Tue Oct  9 22:14:49 2018
Last write time:          Tue Oct  9 22:13:35 2018
Mount count:              25
Maximum mount count:      1
Last checked:             Tue Oct  2 20:25:28 2018
Check interval:           0 (<none>)
Lifetime writes:          179 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:           256
Required extra isize:     32
Desired extra isize:      32
Journal inode:            8
First orphan inode:       1591485
Default directory hash:   half_md4
Directory Hash Seed:      5dcfe344-2b26-4b50-97e1-21952c171d2b
Journal backup:           inode blocks
Checksum type:            crc32c [COLOR=#242729][FONT=Arial][FONT=Consolas]Checksum:                 0x305a8ddb[/FONT]
```
[/FONT][/COLOR]

---

### Post by TheFu on 2018-10-13
You can always boot from alternate media, like a flash drive or dvd, and manually run the fsck off that.
This is a standard troubleshooting method for lots of issues.

Systemd broke the old **sudo touch /forcefsck** method. Too bad.

BTW, 
```
Filesystem state:         clean
```
says fsck isn't likely to help.

---

### Post by Josef_Kotarba on 2019-05-07
[COLOR=#242729][FONT=Arial]I have set the mount count to 1 with tune2fs -c 1 /dev/sda2 and rebooted and still no fsck. It was necessary to wait till the next day, because system runs fsck check obviously only once a day. 
[/FONT][/COLOR]

---

### Post by TheFu on 2019-05-07
> **TheFu said:**
> You can always boot from alternate media, like a flash drive or dvd, and manually run the fsck off that.
This is a standard troubleshooting method for lots of issues. 

Boot from alternate media and manually run the command.

---

