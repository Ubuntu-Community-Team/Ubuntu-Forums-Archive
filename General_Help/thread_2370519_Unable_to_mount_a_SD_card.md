---
title: "Unable to mount a SD card"
date: 2017-09-04
forum: General Help
---

### Post by satimis on 2017-09-04
Hi all,

This is a brand new SD card

&#10219; sudo fdisk -l```

Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000c92e3

Device     Boot Start        End    Sectors   Size Id Type
/dev/sda1        2048 1953523711 1953521664 931.5G 83 Linux

Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00064d3a

Device     Boot     Start        End    Sectors   Size Id Type
/dev/sdb1  *         2048     499711     497664   243M 83 Linux
/dev/sdb2          501758 3907028991 3906527234   1.8T  5 Extended
/dev/sdb5          501760  391124991  390623232 186.3G 83 Linux
/dev/sdb6       391127040  393078783    1951744   953M 82 Linux swap / Solaris
/dev/sdb7       393080832 3907028991 3513948160   1.7T 83 Linux


Disk /dev/sdc: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00009fb6

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdc1  *         2048 217866239 217864192 103.9G 83 Linux
/dev/sdc2       217868286 234440703  16572418   7.9G  5 Extended
/dev/sdc5       217868288 234440703  16572416   7.9G 82 Linux swap / Solaris

Disk /dev/sdd: 59.5 GiB, 63864569856 bytes, 124735488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start       End   Sectors  Size Id Type
/dev/sdd1       32768 124735487 124702720 59.5G  7 HPFS/NTFS/exFAT

```

&#10219; sudo mount -t exfat /dev/sdd1 /media/mycard```

FUSE exfat 1.2.3
ERROR: exFAT file system is not found.

```

exfat-fuse exfat-utils already installed

Please help

Thanks

Regards
satimis

---

### Post by ajgreeny on 2017-09-04
This is going to get completely confusing if you try to continue with this thread and the one at [https://ubuntuforums.org/showthread.php?t=2370488&p=13683078#post13683078](https://ubuntuforums.org/showthread.php?t=2370488&p=13683078#post13683078)

Thread closed
**Please do not create duplicate posts;** it is confusing for all including you and dilutes the forum's ability to help.

---

