---
title: "How to mount sd card that isn't being recognized automatically?"
date: 2012-12-06
forum: General Help
---

### Post by latestversion on 2012-12-06
I have an sd card that I'm trying to mount but it doesn't get recognized automatically like what happens with other sd cards. So I dig some digging and it says that the card (at /dev/mmcblk0, with partition /dev/mmcblk0p1) is 'HPFS/NTFS/exFAT' in the output below:

```
$ sudo fdisk -l /dev/mmcblk0

Disk /dev/mmcblk0: 63.9 GB, 63864569856 bytes
255 heads, 63 sectors/track, 7764 cylinders, total 124735488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot          Start   End          Blocks      Id     System
/dev/mmcblk0p1       32768   124735487    62351360    7      HPFS/NTFS/exFAT

```Trying to mount as NTFS but get error:

```
$ sudo mount -t ntfs /dev/mmcblk0p1 /mnt/sdcard
NTFS signature is missing.
Failed to mount '/dev/mmcblk0p1': Invalid argument
The device '/dev/mmcblk0p1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```Trying to mount as exFAT but get error:

```
$ sudo apt-add-repository ppa:relan/exfat
$ sudo apt-get update
$ sudo apt-get install fuse-exfat

$ sudo mount -t exfat /dev/mmcblk0p1 /mnt/sdcard
FUSE exfat 0.9.8
ERROR: exFAT file system is not found.
```Getting some info about the whole card:

```
$ sudo file -s /dev/mmcblk0
/dev/mmcblk0: x86 boot sector; partition 1: ID=0x7, starthead 10, startsector 32768, 124702720 sectors, extended partition table (last)\011, code offset 0x0
```Getting some info about the partition:

```
$ sudo file -s /dev/mmcblk0p1
/dev/mmcblk0p1: x86 boot sector, code offset 0x52
```

Do you have any idea how I could mount this card successfully?

---

