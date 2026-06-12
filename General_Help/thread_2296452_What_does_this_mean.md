---
title: "What does this mean?"
date: 2015-09-25
forum: General Help
---

### Post by andy140 on 2015-09-25
What does the follow Warning mean? Does this meaning I can only use 1073.7GB?
I can't use  12925.2 GB?And how should I solve it? Thank you very much:)



```

root@BD32:~# fdisk -l


Disk /dev/sda: 1073.7 GB, 1073741627392 bytes
255 heads, 63 sectors/track, 130541 cylinders, total 2097151616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00047b49


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  2097149951  1048324097    5  Extended
/dev/sda5          501760  2097149951  1048324096   8e  Linux LVM


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdb: 12925.2 GB, 12925167403008 bytes
255 heads, 63 sectors/track, 1571395 cylinders, total 25244467584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0aaef052


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT


Disk /dev/mapper/BD32--vg-root: 987.6 GB, 987628568576 bytes
255 heads, 63 sectors/track, 120072 cylinders, total 1928962048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/BD32--vg-root doesn't contain a valid partition table


Disk /dev/mapper/BD32--vg-swap_1: 85.9 GB, 85853208576 bytes
255 heads, 63 sectors/track, 10437 cylinders, total 167682048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/BD32--vg-swap_1 doesn't contain a valid partition table

```

---

### Post by Dennis N on 2015-09-25
With GPT partition tables, you should be using **gdisk** instead of **fdisk**. Try again with gdisk and see what it reports.

---

