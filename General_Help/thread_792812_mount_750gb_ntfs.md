---
title: "mount 750gb ntfs"
date: 2008-05-13
forum: General Help
---

### Post by pepito9 on 2008-05-13
Got a dual boot setup here, id like to access my storage hdd used in XP, i have to mount it manually every time. ive been tinkering with /etc/fstab but get the following error:

[B]Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
[/B]

here is fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b5d652c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       91201   732564000    f  W95 Ext'd (LBA)
/dev/sda5               2       91201   732563968+   7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24502450

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2           12749       20043    58597087+  83  Linux
/dev/sdb3           20044       24177    33206355   83  Linux
/dev/sdb4           24178       24792     4939987+  82  Linux swap / Solaris


also, there is /dev/sdb1 that i think is not being mounted.

here is /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=cdb456ae-401e-441e-8fda-4a149a8b7956 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=dd17ed94-4ecb-4303-9bd9-cb6aebbc4654 /home           ext3    relatime        0       2
# /dev/sdb4
UUID=900937a4-1e03-4fcc-856a-2b2268aae5c4 none            swap    sw              0       0
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda        /media/disco750    ntfs nls=utf8,umask=0222 0 0

that last line is my crappy attempt at it
thanks,

Diego

---

### Post by Nepherte on 2008-05-13
As the error already suggests, you are trying to mount the whole disk instead of a partition. You should probably mount /dev/sda5.

---

### Post by crash91 on 2008-05-16
Yes, as Nepherte said, you should only mount the relevant portion of the disk, so something like this (im not sure if it is ntfs or ntfs-3g, so just put both in, nothing bad will happen:
```
/dev/sda5 /media/disco750 ntfs,ntfs-3g auto,user,noexec,rw,nls=utf8,umask=0222 0 0
```

You should change the "noexec"to "exec" option if you want to be able to execute binaries from it, but this is unlikely. Also im not sure why the "nls=utf8,umask=0222" options are there,if it doesnt work at first try removing them. In your other disks "utf8" is added at the end so maybe aslo try:
```
/dev/sda5 /media/disco750 ntfs,ntfs-3g auto,user,noexec,rw,utf8 0 0
```

If the above doesnt work.

---

