---
title: "e2fsck: Can't allocate dx_block info array"
date: 2013-01-04
forum: General Help
---

### Post by 3DLover on 2013-01-04
I have a md raid 6 with an ext4 partition.  It lost a disk the other day and after rebuiding it with a new disk I get an error with fsck that Google seems to have no reference of: "Can't allocate dx_block info array"  I have no idea what to do next.  Here's the output of a few commands...

```

root@gamut# >more /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
root@gamut# >uname -a
Linux gamut 2.6.31-23-server #75-Ubuntu SMP Fri Mar 18 19:23:09 UTC 2011 x86_64 GNU/Linux
root@gamut# >mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Thu Feb 18 17:31:23 2010
     Raid Level : raid6
     Array Size : 8790862848 (8383.62 GiB 9001.84 GB)
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 14
  Total Devices : 14
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Jan  3 15:55:10 2013
          State : clean
 Active Devices : 14
Working Devices : 14
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : f2155941:5e6a59aa:4ba39cb2:9261f264 (local to host gamut)
         Events : 0.7045548

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1
       6       8      113        6      active sync   /dev/sdh1
       7       8      129        7      active sync   /dev/sdi1
       8       8      145        8      active sync   /dev/sdj1
       9       8      161        9      active sync   /dev/sdk1
      10       8      177       10      active sync   /dev/sdl1
      11       8      193       11      active sync   /dev/sdm1
      12       8      209       12      active sync   /dev/sdn1
      13       8      225       13      active sync   /dev/sdo1
root@gamut# >fdisk -l /dev/md0

WARNING: GPT (GUID Partition Table) detected on '/dev/md0'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: The size of this disk is 9.0 TB (9001843556352 bytes).
DOS partition table format can not be used on drives for volumes
larger than (2199023255040 bytes) for 512-byte sectors. Use parted(1) and GUID
partition table format (GPT).


Disk /dev/md0: 9001.8 GB, 9001843556352 bytes
255 heads, 63 sectors/track, 1094411 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1      267350  2147483647+  ee  GPT
root@gamut# >fsck -Cyf /mnt/md0p1
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
Pass 1: Checking inodes, blocks, and sizes
Inode 441188396, i_size is 3889692672, should be 5029001428992.  Fix? yes

e2fsck: Can't allocate dx_block info array===                        / 56.9%

e2fsck: aborted
root@gamut# >

```

e2fsck dies at 56.9%...  help!

Thanks,
  Ray

---

### Post by 3DLover on 2013-01-07
So to follow up, I found some helpful people on the #ext4 IRC channel, and they suggested adding RAM and increasing the size of my swap file.  FSCK has now passed that 56.9% point where it kept crashing and is proceeding to check the rest of the partition.

---

