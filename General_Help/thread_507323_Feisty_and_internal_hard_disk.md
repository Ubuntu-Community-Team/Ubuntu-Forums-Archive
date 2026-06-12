---
title: "Feisty and internal hard disk"
date: 2007-07-22
forum: General Help
---

### Post by dominiquec on 2007-07-22
Hi, all,

I have two hard disks on my computer, one as my Feisty installation (/dev/sda) and the other as general storage (/dev/sdb).  Both are formatted as ext.

The problem is Feisty does not acknowledge the existence of either /dev/sdb nor any of its partitions (actually just /dev/sdb1) until I run fdisk...and I have to do that every single time.  It's only after I run fdisk that Feisty automatically mounts /dev/sdb1.

Any suggestions on how I can get by without running fdisk each and every time?

Here's a sample dialog:

dom@union:~$ sudo mount /dev/sdb1 Storage
Password:
mount: special device /dev/sdb1 does not exist
dom@union:~$ sudo fdisk -l

Disk /dev/sda: 10.2 GB, 10245537792 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1186     9526513+  83  Linux
/dev/sda2            1187        1245      473917+   5  Extended
/dev/sda5            1187        1245      473886   82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4998    40146403+  83  Linux

dom@union:~$ sudo fdisk /dev/sdb

The number of cylinders for this disk is set to 4998.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
dom@union:~$ 

And at this point, the disk automatically mounts.

---

### Post by dominiquec on 2007-07-22
By the way, I have no such problems with external hard disks.  External hard disks, USB storage media, etc. mount automatically without the need for such gymnastics.

---

