---
title: "Slow Raid 5 to Raid 6 Reshape"
date: 2012-12-09
forum: General Help
---

### Post by moshansky on 2012-12-09
Hello,

Details:
I had 4x2TB drives in the original Raid 5 and am currently moving to 5x2TB Raid 6. However, eventually I want to move to 7x2TB in Raid 6.

I currently have a raid 5 array that is reshaping to a raid 6 but it is taking a brutally long time (ETA: ~8 days). Would it be possible to stop the reshape. Set it back to Raid 5, turn on internal bitmaps, then both grow and reshape, at once, to raid 6? I don't need access to any data during the reshape and just want it to complete as quick as possible. 

I have also followed this post [http://www.cyberciti.biz/tips/linux-raid-increase-resync-rebuild-speed.html]("http://www.cyberciti.biz/tips/linux-raid-increase-resync-rebuild-speed.html") and increased the min and max speed to no avail.

cat /proc/mdstat
```

md0 : active raid6 sdb[0] sdf[6] sdd[4] sdc[3] sda[5]
      5860540272 blocks super 1.2 level 6, 4k chunk, algorithm 18 [5/4] [UUUU_]
      [>....................]  reshape =  2.9% (56696824/1953513424) finish=12196.6min speed=2591K/sec

```

mdadm -D /dev/md0
```

/dev/md0:
        Version : 1.2
  Creation Time : Fri Jun 17 17:28:07 2011
     Raid Level : raid6
     Array Size : 5860540272 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 1953513424 (1863.02 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent

    Update Time : Fri Nov  9 05:09:54 2012
          State : clean, degraded, reshaping
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric-6
     Chunk Size : 4K

 Reshape Status : 2% complete
     New Layout : left-symmetric

           Name : xxxxxxx
           UUID : b4e40e55:90459b4b:a1ea7f7b:b4410b7c
         Events : 226055

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       5       8        0        1      active sync   /dev/sda
       3       8       32        2      active sync   /dev/sdc
       4       8       48        3      active sync   /dev/sdd
       6       8       80        4      spare rebuilding   /dev/sdf

```

---

