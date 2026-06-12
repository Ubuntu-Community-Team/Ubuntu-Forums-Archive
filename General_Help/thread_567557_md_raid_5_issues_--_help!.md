---
title: "md raid 5 issues -- help!"
date: 2007-10-04
forum: General Help
---

### Post by crankharder on 2007-10-04
My 4 disk raid5 array won't come up.  I'm trying to re-add /dev/sdb1 into the array but it continues to come up as a  spare.  

if I try to remove it and add it again like this I get these errors...  Help!!

$ sudo mdadm /dev/md0 --fail /dev/sdb1
mdadm: set device faulty failed for /dev/sdb1:  No such device

$ sudo mdadm /dev/md0 --add /dev/sdb1
mdadm: Cannot open /dev/sdb1: Device or resource busy

 sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Mon Sep 24 21:52:01 2007
     Raid Level : raid5
    Device Size : 488383872 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Oct  4 17:44:47 2007
          State : active, degraded, Not Started
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 128K

           UUID : c3eb0465:c59139df:73d158fc:63c6b3dd (local to host zeus)
         Events : 0.95

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1

       4       8       17        -      spare   /dev/sdb1

---

### Post by crankharder on 2007-10-04
If I shutdown and disconnect /dev/sdb then I can't even start the array....

---

