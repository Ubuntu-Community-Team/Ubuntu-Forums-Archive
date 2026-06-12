---
title: "Raid uuid keeps changing - losing one drive"
date: 2007-09-15
forum: General Help
---

### Post by pnotequalsnp on 2007-09-15
Whenever I restart my machine, one of my four drives is always showing to be missing in my raid 5 assembly.  I use use mdadm -E /dev/sd[b-e]1  to check the drives and find the offline drive always has a different uuid than both the uuid's of the other drives and the uuid of in /etc/mdadm/mdadm.conf.  I then just re-add the missing drive to the array and it rebuilds with no errors.  All four drives are less than a week old, and so far /dev/sdb and /dev/sde have been ejected.  Any ideas?  I would prefer to have my raid 5 working (and not rebuilding).

Below may be some useful info after I reboot and start rebuilding (note: after I started rebuilding the uuid's suddenly match!):  

1. my fstab raid line:
```
 /dev/md0    /media/raid5    auto    defaults    0   0 
```

2. my /etc/mdadm/mdadm.conf:
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=4 spares=1 UUID=97595d63:5c5a4ec4:bb855af7:201184b4
```

3. the command sudo mdadm -E /dev/sd[b-e]1
```

> sudo mdadm -E /dev/sd[b-e]1

/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 97595d63:5c5a4ec4:bb855af7:201184b4 (local to host ubuntu-desktop)
  Creation Time : Thu Sep 13 22:06:40 2007
     Raid Level : raid5
    Device Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Sep 14 22:40:44 2007
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 2368b862 - correct
         Events : 0.6024

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       0        0        3      faulty removed
   4     4       8       65        4      spare   /dev/sde1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 97595d63:5c5a4ec4:bb855af7:201184b4 (local to host ubuntu-desktop)
  Creation Time : Thu Sep 13 22:06:40 2007
     Raid Level : raid5
    Device Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Sep 14 22:40:44 2007
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 2368b874 - correct
         Events : 0.6024

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       0        0        3      faulty removed
   4     4       8       65        4      spare   /dev/sde1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 97595d63:5c5a4ec4:bb855af7:201184b4 (local to host ubuntu-desktop)
  Creation Time : Thu Sep 13 22:06:40 2007
     Raid Level : raid5
    Device Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Sep 14 22:40:44 2007
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 2368b886 - correct
         Events : 0.6024

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       49        2      active sync   /dev/sdd1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       0        0        3      faulty removed
   4     4       8       65        4      spare   /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 97595d63:5c5a4ec4:bb855af7:201184b4 (local to host ubuntu-desktop)
  Creation Time : Thu Sep 13 22:06:40 2007
     Raid Level : raid5
    Device Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Sep 14 22:40:44 2007
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 2368b894 - correct
         Events : 0.6024

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       65        4      spare   /dev/sde1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       0        0        3      faulty removed
   4     4       8       65        4      spare   /dev/sde1

```

---

