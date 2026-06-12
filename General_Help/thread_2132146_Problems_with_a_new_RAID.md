---
title: "Problems with a new RAID"
date: 2013-04-03
forum: General Help
---

### Post by ChadDa3mon on 2013-04-03
I've been trying to get my new NAS up and running, and while it was working at one point, things went to hell after a reboot. I can't tell if one of the drives has an issue, or if I've just really messed something up. I've been doing so much reading up and I have so many dang tabs open I don't even know where to start. Basically, every time I get the raid working and reboot, it comes up in a degraded status. It's always the same drive, /dev/sdf. When I open it in gdisk I get this:
```

Caution! After loading partitions, the CRC doesn't check out!
Warning! Main partition table CRC mismatch! Loaded backup partition table
instead of main partition table!
Warning! One or more CRCs don't match. You should repair the disk!
Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged
****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************
```

I've done the verification and recover, I've done a delete/create, I've nuked the whole thing (extra functionality (experts only) -> z) and created it from scratch again. If I verify the drive, I get this


```
Problem: The CRC for the main partition table is invalid. This table may be
corrupt. Consider loading the backup partition table ('c' on the recovery &
transformation menu). This report may be a false alarm if you've already
corrected other problems.
Identified 1 problems!

```

Any of these will fix the issue for a time, I can assemble the raid and it will recognize the drive, everything seems fine. 

 Here is /dev/sdf1 looking all ready to rock:
```
$ sudo mdadm --examine /dev/sdf1
/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 4da0de52:7f5ff511:34d605fe:dbd36735
           Name : FatCat:0  (local to host FatCat)
  Creation Time : Wed Apr  3 21:53:22 2013
     Raid Level : raid6
   Raid Devices : 6
 Avail Dev Size : 5860064143 (2794.30 GiB 3000.35 GB)
     Array Size : 11720127488 (11177.18 GiB 12001.41 GB)
  Used Dev Size : 5860063744 (2794.30 GiB 3000.35 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 9db843d5:2935545e:d0cddf40:0a1b90c5
    Update Time : Wed Apr  3 22:00:46 2013
       Checksum : 4c4057fb - correct
         Events : 2
         Layout : left-symmetric
     Chunk Size : 128K
   Device Role : Active device 4
   Array State : AAAAAA ('A' == active, '.' == missing)

```


Here I show the raid (should be /dev/md0, that's how it is in mdadm.conf, I've never once assigned /dev/md127) with a bad drive, /dev/sdf1 is removed.
```
$ sudo mdadm --detail /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Wed Apr  3 21:53:22 2013
     Raid Level : raid6
     Array Size : 11720127488 (11177.18 GiB 12001.41 GB)
  Used Dev Size : 2930031872 (2794.30 GiB 3000.35 GB)
   Raid Devices : 6
  Total Devices : 5
    Persistence : Superblock is persistent
    Update Time : Wed Apr  3 22:00:46 2013
          State : clean, degraded
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
         Layout : left-symmetric
     Chunk Size : 128K
           Name : FatCat:0  (local to host FatCat)
           UUID : 4da0de52:7f5ff511:34d605fe:dbd36735
         Events : 2
    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       0        0        4      removed
       5       8       97        5      active sync   /dev/sdg1


```


Stop the incorret /dev/md127
```
$ sudo mdadm --manage /dev/md127 --stop
mdadm: stopped /dev/md127

```


Start it up as it should be
```
$ sudo mdadm --assemble --scan /dev/md0
mdadm: /dev/md0 has been started with 6 drives.

```


Now everything looks great!
```
$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Wed Apr  3 21:53:22 2013
     Raid Level : raid6
     Array Size : 11720127488 (11177.18 GiB 12001.41 GB)
  Used Dev Size : 2930031872 (2794.30 GiB 3000.35 GB)
   Raid Devices : 6
  Total Devices : 6
    Persistence : Superblock is persistent
    Update Time : Wed Apr  3 22:19:49 2013
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0
         Layout : left-symmetric
     Chunk Size : 128K
           Name : FatCat:0  (local to host FatCat)
           UUID : 4da0de52:7f5ff511:34d605fe:dbd36735
         Events : 2
    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1

```


The problem is, this whole cycle will repeat once I reboot my server. I've verified the output of mdadm --detail --scan matches what I have in mdadm.conf

```
$ sudo mdadm --detail --scan
ARRAY /dev/md0 metadata=1.2 name=FatCat:0 UUID=4da0de52:7f5ff511:34d605fe:dbd36735
$ grep ARRAY /etc/mdadm/mdadm.conf
ARRAY /dev/md0 metadata=1.2 name=FatCat:0 UUID=4da0de52:7f5ff511:34d605fe:dbd36735
```

I've also done what I can to verify there are no issues. fsck wouldn't work (I assume because there's no FS on this drive per se, maybe I missed something) but the smart tests pass

```
$ sudo smartctl -d ata -H /dev/sdf
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-26-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```

I just can't slam my head into the desk anymore on this. Either it's some stupid trivial thing (This is my first raid adventure) or /dev/sdf has some bigger issue. I'd greatly appreciate any help.

---

