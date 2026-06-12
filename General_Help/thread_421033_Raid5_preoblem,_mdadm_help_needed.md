---
title: "Raid5 preoblem, mdadm help needed"
date: 2007-04-24
forum: General Help
---

### Post by SundaY82 on 2007-04-24
Hi,

I created a radi5 array using mdadm and that went well, but now mdstat list this.
```
root@mypc:/#cat /proc/mdstat
Personalities : [linear] [raid0] [raid1] [raid10] [raid6] [raid5] [raid4] [faulty]
md0 : active raid5 sda[0] sdd[4] sdc[2] sdb[1]
      1465159488 blocks level 5, 64k chunk, algorithm 2 [4/3] [UUU_]

unused devices: <none>
```
When booting the system report that 3 out of 4 devices are ok just as mdstat but after that it says 1 spare.
So i did some further testing and here are som more output from mdadm:
```
root@mypc:/#mdadm --verbose --verbose --detail --scan
/dev/md0:
        Version : 00.90.03
  Creation Time : Fri Apr  6 16:06:59 2007
     Raid Level : raid5
     Array Size : 1465159488 (1397.29 GiB 1500.32 GB)
    Device Size : 488386496 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Apr 23 20:08:15 2007
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 7a413d5c:15a7fa70:5bc5ef7a:732646c9
         Events : 0.572900

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       0        0        3      removed

       4       8       48        4      active sync   /dev/sdd

----------------------------------------------------
root@mypc:/#mdadm --verbose --verbose --examine --scan
mdadm: No md superblock detected on /dev/md0.
mdadm: No md superblock detected on /dev/hda5.
mdadm: No md superblock detected on /dev/hda2.
mdadm: No md superblock detected on /dev/hda1.
mdadm: No md superblock detected on /dev/hda.
/dev/sdd:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7a413d5c:15a7fa70:5bc5ef7a:732646c9
  Creation Time : Fri Apr  6 16:06:59 2007
     Raid Level : raid5
    Device Size : 488386496 (465.76 GiB 500.11 GB)
     Array Size : 1465159488 (1397.29 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Tue Apr 24 11:01:09 2007
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : b173855f - correct
         Events : 0.572902

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       48        4      active sync   /dev/sdd

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       0        0        3      faulty removed
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7a413d5c:15a7fa70:5bc5ef7a:732646c9
  Creation Time : Fri Apr  6 16:06:59 2007
     Raid Level : raid5
    Device Size : 488386496 (465.76 GiB 500.11 GB)
     Array Size : 1465159488 (1397.29 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Tue Apr 24 11:01:09 2007
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : b173854b - correct
         Events : 0.572902

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       32        2      active sync   /dev/sdc

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       0        0        3      faulty removed
/dev/sdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7a413d5c:15a7fa70:5bc5ef7a:732646c9
  Creation Time : Fri Apr  6 16:06:59 2007
     Raid Level : raid5
    Device Size : 488386496 (465.76 GiB 500.11 GB)
     Array Size : 1465159488 (1397.29 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Tue Apr 24 11:01:09 2007
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : b1738539 - correct
         Events : 0.572902

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       16        1      active sync   /dev/sdb

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       0        0        3      faulty removed
/dev/sda:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7a413d5c:15a7fa70:5bc5ef7a:732646c9
  Creation Time : Fri Apr  6 16:06:59 2007
     Raid Level : raid5
    Device Size : 488386496 (465.76 GiB 500.11 GB)
     Array Size : 1465159488 (1397.29 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Tue Apr 24 11:01:09 2007
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0
       Checksum : b1738527 - correct
         Events : 0.572902

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        0        0      active sync   /dev/sda

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       0        0        3      faulty removed
```

I cant figure out if some disk is broken or not, and if so whitch one?

And as it reports 1 spare on boot, can i resync the array somehow to get them all online again?

I would really appreciate if someone could help me out here.

Thanks!
//Ola

---

### Post by SundaY82 on 2007-04-24
it looks like it thinks there are 5 devices if i check the output from, mdadm -D /dev/md0
```
    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       0        0        3      removed

       4       8       48        4      active sync   /dev/sdd
```
how can i remove device 3? 
when i created the raid i know i just choosed those four devices.

I also tried this:
stop the array
```
mdadm --stop --scan
```
and then assemble again
```
mdadm --assemble --run --force --update=resync /dev/md0 /dev/sda /dev/sdb /dev/sdc /dev/sdd
mdadm: clearing FAULTY flag for device 3 in /dev/md0 for /dev/sdd
mdadm: /dev/md0 has been started with 3 drives (out of 4) and 1 spare.
```
This clearly doesnt remove the device, any other suggestions?

Im very new to linux raid ;)

---

