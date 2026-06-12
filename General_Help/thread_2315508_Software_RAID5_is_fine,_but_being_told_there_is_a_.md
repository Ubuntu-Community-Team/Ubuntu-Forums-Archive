---
title: "Software RAID5 is fine, but being told there is a problem"
date: 2016-02-29
forum: General Help
---

### Post by Roy_Beck on 2016-02-29
Brief history:

Ubuntu server 14.04.3
4X1.5 TB WD drives - originally created as a software RAID 10
Deleted the RAID 10 array and created RAID-5 (working fine with no issues)
But now every day I am being notified the following (via the cron.daily report):
[FONT=arial]
mdadm: Unknown keyword devices=/dev/sdb1,/dev/sdc1,/[/FONT][FONT=arial]dev/sdd1,/dev/sde1

I run [/FONT]mdadm -D /dev/md0 and get this:

mdadm: Unknown keyword devices=/dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sde1
/dev/md0:
        Version : 1.2
  Creation Time : Fri Feb 26 22:09:43 2016
     Raid Level : raid5
     Array Size : 4395018240 (4191.42 GiB 4500.50 GB)
  Used Dev Size : 1465006080 (1397.14 GiB 1500.17 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent


    Update Time : Mon Feb 29 11:15:40 2016
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : TRINITY:0  (local to host TRINITY)
           UUID : f7474b0a:a0a94417:97225e8f:80385f71
         Events : 40291


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       4       8       65        3      active sync   /dev/sde1

So there doesn't appear to be anything wrong with the new array...thinking this is a leftover from the old RAID 10?
If so, how do I stop it?

Thank you for any help,

Roy

---

