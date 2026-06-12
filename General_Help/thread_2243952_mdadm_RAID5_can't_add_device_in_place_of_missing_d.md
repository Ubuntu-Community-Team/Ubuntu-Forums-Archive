---
title: "mdadm RAID5 can't add device in place of missing device"
date: 2014-09-12
forum: General Help
---

### Post by akos.maroy on 2014-09-12
Hi,

I have a RAID5 array with 4 disks, where one of the disks have been removed. I'm trying to add a disk in place of this, but for some reason the 'usual' --add doesn't work:

```
# mdadm /dev/md0 --add /dev/sda1
mdadm: add new device failed for /dev/sda1 as 5: Invalid argument

```

from the part of the message 'as 5' it seems to me that it doesn't actually want to add this device in place of the missing one, but instead as a 5th device?

additional info:

```
# cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md0 : active raid5 sdc1[7] sdd1[4] sdb1[6]
      5860531200 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [UU_U]
      
unused devices: <none>
# mdadm -Q /dev/md0
/dev/md0: 5589.04GiB raid5 4 devices, 0 spares. Use mdadm --detail for more detail.
# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Mon Feb 20 08:05:57 2012
     Raid Level : raid5
     Array Size : 5860531200 (5589.04 GiB 6001.18 GB)
  Used Dev Size : 1953510400 (1863.01 GiB 2000.39 GB)
   Raid Devices : 4
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Fri Sep 12 13:31:45 2014
          State : clean, degraded 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : rakku:0
           UUID : a56634e9:9a26c4d4:1a7a4d23:b34545ab
         Events : 69203

    Number   Major   Minor   RaidDevice State
       7       8       33        0      active sync   /dev/sdc1
       6       8       17        1      active sync   /dev/sdb1
       2       0        0        2      removed
       4       8       49        3      active sync   /dev/sdd1

```

so it seems that device number 2 (third in line) is marked as removed, but I can't just add a device in place of it.

the partition at /dev/sda1 is of the very same size as the other partitions, so that should not be a problem.

is there some 'magic' to be used when initializing a new device? of course /dev/sdc1, /dev/sdb1 and /dev/sdd1 contains valid RAID 1.2 superblocks, wheras /dev/sda1 of course doesnt:

```
# mdadm -E /dev/sda1
mdadm: No md superblock detected on /dev/sda1.
# mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : a56634e9:9a26c4d4:1a7a4d23:b34545ab
           Name : rakku:0
  Creation Time : Mon Feb 20 08:05:57 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907025072 (1863.01 GiB 2000.40 GB)
     Array Size : 5860531200 (5589.04 GiB 6001.18 GB)
  Used Dev Size : 3907020800 (1863.01 GiB 2000.39 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 38067b22:c6619983:c1f37909:d8480a6b

    Update Time : Fri Sep 12 13:31:45 2014
       Checksum : 3041a2e7 - correct
         Events : 69203

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AA.A ('A' == active, '.' == missing)

```

---

