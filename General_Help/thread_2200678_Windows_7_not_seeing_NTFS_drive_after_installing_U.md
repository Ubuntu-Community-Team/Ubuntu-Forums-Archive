---
title: "Windows 7 not seeing NTFS drive after installing Ubuntu"
date: 2014-01-20
forum: General Help
---

### Post by dani-valverde on 2014-01-20
Hello,
Last week I has to do a fresh Ubuntu  12.04 install. This is my partition table:
```
Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x032c713c


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   500115455   249954304    7  HPFS/NTFS/exFAT


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xfa1c6042


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907028991  1953513472    7  HPFS/NTFS/exFAT


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001d306


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048  3873595391  1936796672   83  Linux
/dev/sdc2      3873597438  3907028991    16715777    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sdc5      3873597440  3907028991    16715776   82  Linux swap / Solaris

```
Where sda is a Windows 7 SSD HDD, sdb is a 2 Tb NTFS HDD and sdc is an Ubuntu system on a 2Tb HDD. From Ubuntu I can see all the drives. However, from Windows 7 I can only see sda, and I also want to be able to work with sdb, that's why it is formatted as NTFS. Can anyone help me?
Thanks,

Dani

---

