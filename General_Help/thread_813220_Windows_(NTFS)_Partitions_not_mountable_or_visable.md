---
title: "Windows (NTFS) Partitions not mountable or visable."
date: 2008-05-30
forum: General Help
---

### Post by liammarksmith on 2008-05-30
Untill now i thought, Great ubuntu going well no problems at all part from a few tweaks with my Dell Wireless Drivers nothing will stop me from using Ubuntu.

All of a sudden i booted up and i cannot see Windows Partitions on my Desktop, I thought they must not be mounted, I went into the Computer and they are still not there?

Is there anyway i can mount them and get them back?

I appreciate  your help,
Liam Smith

---

### Post by ibuclaw on 2008-05-30
Open up a terminal and type in:
```
sudo mount -a
```
If nothing happens, can you post the output of this:
```
cat /etc/fstab | grep ntfs
```

Regards
Iain

---

### Post by cdtech on 2008-05-30
Sure!

sudo fdisk -l will list all the drives Ubuntu see's, then we can show you how to mount them.

Are you dual booting with windows?

---

### Post by liammarksmith on 2008-05-31
Ok i tried the first method and this is my outcome:

> 
liams@liams-laptop:~$ sudo mount -a
[sudo] password for liams:
mount: according to mtab, /dev/sda2 is already mounted on /media/sda2

FUSE mount point creation failed
Unmounting /dev/sda2 (RECOVERY)
mount: according to mtab, /dev/sda5 is already mounted on /media/sda5

FUSE mount point creation failed
Unmounting /dev/sda5 (Windows)
liams@liams-laptop:~$ 
liams@liams-laptop:~$ cat /etc/fstab | grep ntfs
UUID=EADCC260DCC22723 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
UUID=3C9CDDDA9CDD8F30 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
liams@liams-laptop:~$ 

This has not mounted the drive at all.

So i tried tinivole's way and here is my outcome:

> liams@liams-laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          14      112423+  16  Hidden FAT16
/dev/sda2   *          15        1320    10490260    7  HPFS/NTFS
/dev/sda3            1321        7296    48002220    f  W95 Ext'd (LBA)
/dev/sda5            1321        4705    27189981    7  HPFS/NTFS
/dev/sda6            7183        7296      915673+  82  Linux swap / Solaris
/dev/sda7            4706        7182    19896471   83  Linux

Partition table entries are not in disk order
liams@liams-laptop:~$ 


I want /dev/sda5 Mounted im not too bothered about sda2 as it is a recovery drive.

In /media/ sda5 exists which i believe is the problem as i can't eject it - Its not mounted but i can't mount because it thinks its mounted.

---

