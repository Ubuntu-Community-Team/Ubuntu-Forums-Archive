---
title: "degraded raid"
date: 2013-05-01
forum: General Help
---

### Post by 65 mustang on 2013-05-01
I am getting a message that my systems raid has a problem at startup.  Although when i go ahead and start with a degraded raid i cannot find that is it degraded.  This has happened before but i always can see the raid in degraded condition upon boot.

```
root@dalserver:~# mdadm --detail /dev/md0 
/dev/md0:
        Version : 0.90
  Creation Time : Wed Sep 22 19:13:15 2010
     Raid Level : raid5
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 6
  Total Devices : 7
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed May  1 21:29:22 2013
          State : clean 
 Active Devices : 6
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 7764302f:355fe475:aa94e06e:3a63582b
         Events : 0.32795

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       65        2      active sync   /dev/sde1
       3       8       81        3      active sync   /dev/sdf1
       4       8       97        4      active sync   /dev/sdg1
       5       8        1        5      active sync   /dev/sda1

       6       8      113        -      spare   /dev/sdh1
root@dalserver:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdh1[6](S) sdg1[4] sdf1[3] sde1[2] sdc1[1] sdb1[0] sda1[5]
      4883799680 blocks level 5, 64k chunk, algorithm 2 [6/6] [UUUUUU]
      
unused devices: <none>
```

Where else can i look for more information?  Any good logs?

---

### Post by SaturnusDJ on 2013-05-02
Maybe the definition in /etc/mdadm/mdadm.conf isn't right. Fix it or leave it, then run
```

update-initramfs -u
``` to send the config to the bootloader stuff. (Maybe that one isn't proper.)

For logs check /var/log/kern.log

---

