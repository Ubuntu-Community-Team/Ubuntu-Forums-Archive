---
title: "mdadm (RAID5) Degraded Array (removed disc)"
date: 2013-11-05
forum: General Help
---

### Post by minger_88 on 2013-11-05
I have been having terrible performance from a RAID5 made of 3, 2-TB drives. Doing some googling, I got to using some of the inquery commands and see that I'm having issues with the array. Now, I decided on that RAID configuration because I read about the (marginal) redundancy that I would have, so I hope all is not lost. Here are various outputs, I hope someone can point me in the right direction

**cat /proc/mdstat **
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sde1[3] sdd1[1]
      3907023872 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [_UU]
      
unused devices: <none>

```

**sudo mdadm --examine /dev/sd[b,c,d,e]1**
```
 
/dev/sdb1:
   MBR Magic : aa55
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 31bacfd1:998e71ee:704e9500:29f029b7
           Name : mike-server:0  (local to host mike-server)
  Creation Time : Fri Aug 10 12:32:38 2012
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 3907023872 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : d0a3dc06:8748b9da:c5e34264:da2ef55f

    Update Time : Sat Aug 31 00:19:18 2013
       Checksum : 4c8c1ba0 - correct
         Events : 91328

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAA ('A' == active, '.' == missing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 31bacfd1:998e71ee:704e9500:29f029b7
           Name : mike-server:0  (local to host mike-server)
  Creation Time : Fri Aug 10 12:32:38 2012
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 3907023872 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 8c9f85c3:2f9fb0fd:c0c9d302:6a68c215

    Update Time : Tue Nov  5 20:50:37 2013
       Checksum : 80e45aaa - correct
         Events : 131129

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : .AA ('A' == active, '.' == missing)
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 31bacfd1:998e71ee:704e9500:29f029b7
           Name : mike-server:0  (local to host mike-server)
  Creation Time : Fri Aug 10 12:32:38 2012
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 3907023872 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : e74bafe9:bcabfbc8:15f40bce:f41dae32

    Update Time : Tue Nov  5 20:50:37 2013
       Checksum : 5a7cf374 - correct
         Events : 131129

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : .AA ('A' == active, '.' == missing)


```

**sudo mdadm --detail /dev/md0**
```

/dev/md0:
        Version : 1.2
  Creation Time : Fri Aug 10 12:32:38 2012
     Raid Level : raid5
     Array Size : 3907023872 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 3
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Tue Nov  5 20:46:47 2013
          State : clean, degraded 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : mike-server:0  (local to host mike-server)
           UUID : 31bacfd1:998e71ee:704e9500:29f029b7
         Events : 131127

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       49        1      active sync   /dev/sdd1
       3       8       65        2      active sync   /dev/sde1

```

---

### Post by SaturnusDJ on 2013-11-06
```
mdadm --manage /dev/md0 --re-add /dev/sdc1
```
else
```
mdadm --manage /dev/md0 --add /dev/sdc1
```

Ok that was a bit short. :P

You have RAID5, so one disk is allowed to be missing. You can still access your data now. With the above commands you bring back the third disk in the array.
Be sure to have make backups, cause RAID really is no backup. Adding back a dropped disk, or replacing a failed disk creates so much reads/writes that sometimes another disk fails, while the array is degraded...then it can really be game over.

---

### Post by XBNCPRk on 2013-11-06
Before readding the dropped drive, it might be wise to quickly check the smart tools info on it and make sure theres not a problem with the drive itself. Syncing a dying drive back into an otherwise functional (albeit degraded) array is bad juju.

---

### Post by SaturnusDJ on 2013-11-06
Oh good idea yeah.

I thought he took the third one out on purpose. Not much background information in topic start.

---

### Post by minger_88 on 2013-11-06
My apologies -- yea I didn't remove the drive, it's still physically in the system. Data is accessible, though it seems very slowly. I will check the smart status and reply. Thanks so far, I appreciate it.

---

### Post by minger_88 on 2013-11-06
OK, so the smart stuff seemed ...

```

sudo smartctl -H /dev/sdc
[sudo] password for michael: 
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-23-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```

Based on this, I went ahead and readded the drive. I wasn't able to use the re-add command, but was able to "add"
```

$ sudo mdadm --manage /dev/md0 --re-add /dev/sdc1
mdadm: --re-add for /dev/sdc1 to /dev/md0 is not possible
$ sudo mdadm --manage /dev/md0 --add /dev/sdc1
mdadm: added /dev/sdc1

```

Now it seems to be doing something ...
```

$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdc1[4] sde1[3] sdd1[1]
      3907023872 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [_UU]
      [>....................]  recovery =  0.0% (548996/1953511936) finish=12413.6min speed=2621K/sec
      
unused devices: <none>

```

I seem to recall this happening before. Would it be true to say that when a drive fails  S.M.A.R.T. will give me some sort or error?

---

### Post by XBNCPRk on 2013-11-06
Yes, if the drive is popping bad sectors or having other issues it will not have passed.

That said, something like 1/3 of disks fail without ever having reported a smart error first. Those though are almost always in my experience drive fatalities... theres nothing useful to do after with those disks except hope theyre still under warranty, or target practice.

Also, the progress youre seeing on /proc/mdstat is it resyncing that drive back into the array; checking the data integrity as it goes. 2mbps though is a fair bit slow... typically I see rebuild speeds more like ~80mbps (starts at 120ish finishes at 40ish). If youre using the drives while rebuilding the array, it will slow it down dramatically, so if possible avoid doing so. 

Has any progress been made as to why the drive was kicked from the array to start with?

---

