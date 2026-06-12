---
title: "[SOLVED] mounting windows partititions"
date: 2008-02-19
forum: General Help
---

### Post by vikasmk on 2008-02-19
My windows is of ntfs file system . It automatically gets mounted most of the times. 
but sometimes all i can use is ubuntu home folder . whats wrong???
 
 OUt put of sudo fdisk -l is 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05f405f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        9728    67898722+   f  W95 Ext'd (LBA)
/dev/sda5            1276        3825    20482843+   7  HPFS/NTFS
/dev/sda6   *        3826        6135    18555043+  83  Linux
/dev/sda7            6376        9728    26932941    7  HPFS/NTFS
/dev/sda8            6136        6375     1927768+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1031 MB, 1031798784 bytes
32 heads, 63 sectors/track, 999 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x2b73117f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1000     1007584+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(998, 31, 63) logical=(999, 19, 51)

---

### Post by northern lights on 2008-02-19
NTFS, as well as other filesystems, can be marked as unclean. Most likely cause is a previous improper shutdown of windows (It crashed or you just flicked the switch). Resizing the partition has the same effect. Linux doesn't like unclean partitions at all and one thing it refuses to do with 'em is mount the bastards. Upon booting however, Windows checks the filesystem and marks it clean, so almost always booting up Windows and rebooting into Ubuntu fixes the problem.

---

### Post by PmDematagoda on 2008-02-19
Are you able to mount the NTFS partitions manually?

---

