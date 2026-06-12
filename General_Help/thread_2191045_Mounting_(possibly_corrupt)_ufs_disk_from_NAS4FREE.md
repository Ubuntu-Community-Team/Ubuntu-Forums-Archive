---
title: "Mounting (possibly corrupt) ufs disk from NAS4FREE"
date: 2013-11-30
forum: General Help
---

### Post by kishspatel90 on 2013-11-30
[COLOR=#333333][FONT=UbuntuRegular][SIZE=2][FONT=arial]I have a hard disk that I was previously using in a system installed with NAS4FREE. Unfortunately, the system seemed to stop working and, if possible, I would like to retrieve some files from the hard disk.
I've booted the system into ubuntu through a live CD, but I'm having trouble mounting the disk. I'm still new to ubuntu so I don't understand much of it. This is the output I get from sudo fdisk -l :
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     4080509     2040223+  a5  FreeBSD
Partition 1 does not start on physical sector boundary.
/dev/sda2         4080510  1949439554   972679522+  a5  FreeBSD
Partition 2 does not start on physical sector boundary.
/dev/sda3      1949439555  1953520064     2040255   a5  FreeBSD
Partition 3 does not start on physical sector boundary.
```
Following another thread, I also tried dmesg | grep bsd and got:
```
ubuntu@ubuntu:~$ dmesg|grep bsd 
[    6.668810]  sda1: <bsd: sda5 > 
[    6.668810]  sda2: <bsd:bad subpartition - ignored
```
I've tried the command sudo mount -r -t ufs -o ufstype=ufs2 /dev/sda5 /usr/disk (where /usr/disk is a directory I have created) but this doesn't work. Does anyone have any solutions/suggestions?
Thanks.

[/FONT][/SIZE]
[/FONT][/COLOR]

---

