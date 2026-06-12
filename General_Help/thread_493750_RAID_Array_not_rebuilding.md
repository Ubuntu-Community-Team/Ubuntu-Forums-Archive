---
title: "RAID Array not rebuilding"
date: 2007-07-06
forum: General Help
---

### Post by Rob_Quads on 2007-07-06
Recently my machine had a few issues with its RAID array. Not sure what caused it as they were all new discs. I have now got the array into a strange situation which I cannot resolve.

All 6 discs are available but for some reason the array is marking the replacement discs as spare even though they have all the raid data on them. Anyone know how to get it to recognise these drive as active and not spare?

mdadm --detail /md0 gives

```

/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Jun 24 16:01:57 2007
     Raid Level : raid5
  Used Dev Size : 244198464 (232.89 GiB 250.06 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jul  6 09:07:58 2007
          State : clean, degraded, Not Started
 Active Devices : 4
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 2

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 223dc2d4:90d7cd44:0ed5af93:957792cd (local to host FileServer)
         Events : 0.186604

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       80        1      active sync   /dev/sdf
       2       8       96        2      active sync   /dev/sdg
       3       8      112        3      active sync   /dev/sdh
       4       0        0        4      removed
       5       8      144        5      active sync   /dev/sdj

       6       8      128        -      spare   /dev/sdi
       7       8       64        -      spare   /dev/sde

```

---

