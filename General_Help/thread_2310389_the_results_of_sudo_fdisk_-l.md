---
title: "the results of sudo fdisk -l"
date: 2016-01-18
forum: General Help
---

### Post by Lou Reed on 2016-01-18
I am trying to understand all of the different drives that I have and how they translate when fdisk -l is used.

the output is


```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76692ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      264191      131072    b  W95 FAT32
/dev/sda2          264192    34811903    17273856   83  Linux
/dev/sda3   *    34812855   976771119   470979132+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 34.4 GB, 34351349760 bytes
255 heads, 63 sectors/track, 4176 cylinders, total 67092480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008f517

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          96    67092479    33546192    c  W95 FAT32 (LBA)

Disk /dev/sdc: 32.0 GB, 32018268160 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62535680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            8192    31101839    15546824    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ mkdir mnt
ubuntu@ubuntu:~$ 

```


Now I have a a hard drive conmected to with Windows 7 on it.I have an Ubuntu LiveCd (that I booted off of)
with a thumb drive of 32 GB capacity and finally a micro-sd card with 32 GB it is connected through an adapter
obviuosly.

I need to know what /dev/sda1, /dev/sda2, /dev/sda3/ and /dev/sdb and /dev/sdb are. I think I know some of them, but I do not know all of them.

Any help appreciated. 

Respectfully,

Newport_j

---

### Post by bab1 on 2016-01-18
> **James_M._Yunker said:**
> I am trying to understand all of the different drives that I have and how they translate when fdisk -l is used.

the output is


```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76692ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      264191      131072    b  W95 FAT32
/dev/sda2          264192    34811903    17273856   83  Linux
/dev/sda3   *    34812855   976771119   470979132+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 34.4 GB, 34351349760 bytes
255 heads, 63 sectors/track, 4176 cylinders, total 67092480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008f517

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          96    67092479    33546192    c  W95 FAT32 (LBA)

Disk /dev/sdc: 32.0 GB, 32018268160 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62535680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            8192    31101839    15546824    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ mkdir mnt
ubuntu@ubuntu:~$ 

```


Now I have a a hard drive conmected to with Windows 7 on it.I have an Ubuntu LiveCd (that I booted off of)
with a thumb drive of 32 GB capacity and finally a micro-sd card with 32 GB it is connected through an adapter
obviuosly.

I need to know what /dev/sda1, /dev/sda2, /dev/sda3/ and /dev/sdb and /dev/sdb are. I think I know some of them, but I do not know all of them.

Any help appreciated. 

Respectfully,

Newport_j
The device (/dev) is the physical drive.  The first drive enumerated is sda (/dev/sda) and the partitions are the numbers (/dev/sda/1,2,3 etc).  In your case there are 3 devices (sda, sdb, and sdc) the first one has 3 partitions while the other 2 each have 1 partition of the entire device.

While the there is no absolute way of knowing what is on a partition using fdisk.  This is lower level info than files and directories.  You can surmise what is there.

These days the tool ***parted*** is preferred as it will accommodate larger disks and human readable disk and partition sizes.  Try this command to see the same disks```
sudo parted -l 
```

---

