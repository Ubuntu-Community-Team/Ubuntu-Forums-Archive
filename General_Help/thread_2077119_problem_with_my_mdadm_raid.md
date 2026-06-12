---
title: "problem with my mdadm raid"
date: 2012-10-27
forum: General Help
---

### Post by dexter123 on 2012-10-27
Hello Members,

I had two disks 2TB and 1.5 TB which I created a raid1 mdadm array with. 1.5TB each both drives. I thought I had this working until i found that my raid will not take more than around 250GBs. I must have done something wrong here..Please help check these outputs:

xx@desktop:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid1] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[1] sdc1[0]
      1465031488 blocks [2/2] [UU]
      
unused devices: <none>

--------------------------------------------------------------------

xx@desktop:~$ sudo fdisk -l 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfe997754

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60056   482399788+  83  Linux
/dev/sda2           60057       60801     5984212+   5  Extended
/dev/sda5           60057       60801     5984181   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000581b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182388  1465031578+  83  Linux
Partition 1 does not start on physical sector boundary.

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000171b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182388  1465031578+  83  Linux

Disk /dev/md0: 1500.2 GB, 1500192243712 bytes
2 heads, 4 sectors/track, 366257872 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table


------------------------------------------------

xx@desktop:~$sudo fdisk -l /dev/sdc1

Disk /dev/sdc1: 1500.2 GB, 1500192336384 bytes
255 heads, 63 sectors/track, 182387 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc1 doesn't contain a valid partition table

------------------------------------------------------------------------

xx@desktop:~$ sudo fdisk -l /dev/sdb1

Disk /dev/sdb1: 1500.2 GB, 1500192336384 bytes
255 heads, 63 sectors/track, 182387 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb1 doesn't contain a valid partition table


-----------------------------------------------------------------------------

xx@desktop:~$ sudo mdadm --query --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sun Sep  9 08:17:25 2012
     Raid Level : raid1
     Array Size : 1465031488 (1397.16 GiB 1500.19 GB)
  Used Dev Size : 1465031488 (1397.16 GiB 1500.19 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Oct 27 14:23:36 2012
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 93704abd:272c8e97:46df5ee0:20622b71
         Events : 0.68

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       17        1      active sync   /dev/sdb1

---

