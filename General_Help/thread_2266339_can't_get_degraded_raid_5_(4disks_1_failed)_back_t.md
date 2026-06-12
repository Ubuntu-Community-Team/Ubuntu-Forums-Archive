---
title: "can't get degraded raid 5 (4disks 1 failed) back to work"
date: 2015-02-22
forum: General Help
---

### Post by martin147 on 2015-02-22
Had an error while trying to backup files from a degraded system. Now assembling it doesn't work anymore.
Would be great if someone could help me out here. I'm not to experience with raids but would really need to get the raid with it's current data back to work.

would a mdadm -C be save in this situation? like:
```
mdadm -C /dev/md0 -e 1.0 --level 5 -n 4 --chunk 64 --assume-clean \     /dev/sda3 /dev/sdb3 /dev/sdc3 missing 
```
```

# mdadm --assemble /dev/md0 /dev/sda3 /dev/sdb3 /dev/sdc3
mdadm: failed to RUN_ARRAY /dev/md0: Input/output error
# cat /proc/mdstat
Personalities : [linear] [raid0] [raid1] [raid10] [raid6] [raid5] [raid4]
md0 : inactive sda3[0] sdc3[2] sdb3[1]
      8786092668 blocks super 1.0
```

additional information:
```
[/mnt/ext] # cat /etc/mdadm.conf
ARRAY /dev/md9 level=raid1 num-devices=4 UUID=9f3f6022:26ccb4e4:aaa70578:716896d2
ARRAY /dev/md4 level=raid1 num-devices=2 UUID=3fd5a9d1:33c64e9e:f8b2d041:53d87cb3
   spares=1
ARRAY /dev/md/0 level=raid5 metadata=1.0 num-devices=4 UUID=da649128:e7b1becc:c830c335:63252302 name=0
ARRAY /dev/md13 level=raid1 num-devices=4 UUID=c11e2bd9:0b0b0de8:238c15c3:31fa7cc9
```
```
[/mnt/ext] # mdadm -E /dev/sd[abcd]3
/dev/sda3:
          Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x0
     Array UUID : da649128:e7b1becc:c830c335:63252302
           Name : 0
  Creation Time : Mon Jul 30 14:31:13 2012
     Raid Level : raid5
   Raid Devices : 4

  Used Dev Size : 5857395112 (2793.02 GiB 2998.99 GB)
     Array Size : 17572185216 (8379.07 GiB 8996.96 GB)
      Used Size : 5857395072 (2793.02 GiB 2998.99 GB)
   Super Offset : 5857395368 sectors
          State : clean
    Device UUID : 2ae77c49:b48601dd:e9b0b61a:d1cb4a5a

    Update Time : Sat Feb 21 18:37:49 2015
       Checksum : 2e42882b - correct
         Events : 15222

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 0 (0, 1, 2, failed)
   Array State : Uuu_ 1 failed
/dev/sdb3:
          Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x0
     Array UUID : da649128:e7b1becc:c830c335:63252302
           Name : 0
  Creation Time : Mon Jul 30 14:31:13 2012
     Raid Level : raid5
   Raid Devices : 4

  Used Dev Size : 5857395112 (2793.02 GiB 2998.99 GB)
     Array Size : 17572185216 (8379.07 GiB 8996.96 GB)
      Used Size : 5857395072 (2793.02 GiB 2998.99 GB)
   Super Offset : 5857395368 sectors
          State : active
    Device UUID : 2dc4afdb:a910fdd6:7d3229f8:6cdb9009

    Update Time : Sat Feb 21 18:38:33 2015
       Checksum : 47297f81 - correct
         Events : 15223

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 1 (0, 1, 2, failed)
   Array State : uUu_ 1 failed
/dev/sdc3:
          Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x0
     Array UUID : da649128:e7b1becc:c830c335:63252302
           Name : 0
  Creation Time : Mon Jul 30 14:31:13 2012
     Raid Level : raid5
   Raid Devices : 4

  Used Dev Size : 5857395112 (2793.02 GiB 2998.99 GB)
     Array Size : 17572185216 (8379.07 GiB 8996.96 GB)
      Used Size : 5857395072 (2793.02 GiB 2998.99 GB)
   Super Offset : 5857395368 sectors
          State : active
    Device UUID : e94d492d:27fea4b5:1f4fac0e:98e4838e

    Update Time : Sat Feb 21 18:38:33 2015
       Checksum : 12e11c89 - correct
         Events : 15223

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 2 (0, 1, 2, failed)
   Array State : uuU_ 1 failed
mdadm: cannot open /dev/sdd3: No such device or address
```
```
[/mnt/ext] # mdadm -D /dev/md0
/dev/md0:
        Version : 01.00.03
  Creation Time : Mon Jul 30 14:31:13 2012
     Raid Level : raid5
  Used Dev Size : 2928697536 (2793.02 GiB 2998.99 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Feb 21 18:38:33 2015
          State : active, degraded, Not Started
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           Name : 0
           UUID : da649128:e7b1becc:c830c335:63252302
         Events : 15222

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3
       2       8       35        2      active sync   /dev/sdc3
       3       0        0        3      removed
```
```
[~] # cat /proc/partitions
major minor  #blocks  name

  31        0        512 mtdblock0
  31        1       2048 mtdblock1
  31        2       9216 mtdblock2
  31        3       3072 mtdblock3
  31        4        256 mtdblock4
  31        5       1280 mtdblock5
   8        0 2930266584 sda
   8        1     530125 sda1
   8        2     530142 sda2
   8        3 2928697693 sda3
   8        4     498012 sda4
   8       16 2930266584 sdb
   8       17     530125 sdb1
   8       18     530142 sdb2
   8       19 2928697693 sdb3
   8       20     498012 sdb4
   8       32 2930266584 sdc
   8       33     530125 sdc1
   8       34     530142 sdc2
   8       35 2928697693 sdc3
   8       36     498012 sdc4
   8       48 2930266584 sdd
```

---

