---
title: "USB External Sata drive not mounting on plug-in"
date: 2008-02-11
forum: General Help
---

### Post by herbster on 2008-02-11
```
bobby@dabox:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00068810

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           58252       60801    20482875    7  HPFS/NTFS
/dev/sda2               1       58251   467901126   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008577e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xefa17447

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde9fde9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sdd2            7650        8924    10241437+  83  Linux
/dev/sdd3            8925       12748    30716280   83  Linux
/dev/sdd4           12749       60801   385985722+   5  Extended
/dev/sdd5           12749       13258     4096543+  82  Linux swap / Solaris
/dev/sdd6           13259       60801   381889116   83  Linux
bobby@dabox:~$
```
The drive is sda and partition 2, sda2. It doesn't automount when plugged in.

/etc/fstab:
```
bobby@dabox:~$ cat /etc/fstab
# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0


#/dev/cdrom /mnt/cdrom   iso9660   ro,user,noauto,unhide   0      0
#/dev/cdrom1 /mnt/cdrom1   iso9660   ro,user,noauto,unhide   0      0
#/dev/dvd /mnt/dvd   udf   ro,user,noauto,unhide   0      0
/dev/sdd2 / ext3 defaults 0 1
/dev/sdd3 /home ext3 defaults 0 1
/dev/sdd5 swap swap defaults 0 0
 /dev/sdd1 /media/xp ntfs ro,nls=utf8,umask=0222 0 0
```
I am plugging it in via eSata, is this the issue? It reads it fine in fdisk as can see.

I use HAL and have it in daemons on startup. I also belong to hal and dbus and storage groups. Also have thunar-volman on startup.

---

