---
title: "RAID array keeps failing -"
date: 2007-08-16
forum: General Help
---

### Post by Rob_Quads on 2007-08-16
I am getting problems with my software raid arrays. I have two arrays which often upon reboot are unactive. I have no idea what is causing the array to stop. 

```

fred@FileServer:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sde1[0] sdj1[5] sdi1[4] sdh1[3] sdg1[2] sdf1[1]
      1220979520 blocks level 5, 64k chunk, algorithm 2 [6/6] [UUUUUU]

md2 : inactive sda1[0](S) sdd1[3](S) sdc1[2](S) sdb1[1](S)
      1172166272 blocks

```
If I try and start the array I get 
```

fred@FileServer:~$ sudo mdadm --run /dev/md2
mdadm: failed to run array /dev/md2: Input/output error

```
Below are the details of the array

```

/dev/md2:
        Version : 00.90.03
  Creation Time : Tue Jun 26 23:17:57 2007
     Raid Level : raid5
  Used Dev Size : 293033536 (279.46 GiB 300.07 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Thu Aug 16 12:27:43 2007
          State : active, degraded, Not Started
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 5006a6b2:ceeae0ec:d484c166:6e86c3d7
         Events : 0.445

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       0        0        2      removed
       3       8       49        3      active sync   /dev/sdd1

```

So Any idea what could be causing this to happen. Every so often all the drives get marked as (S)

---

### Post by fjgaude on 2007-08-16
Can't say for sure what is wrong... you mount the arrays in fstab? The man mdadm pages give much in the way fo guidance to understand what could be wrong, eh?

```
sudo mdadm --run --query /dev/md2
```

What does this command show?

frank

---

### Post by Rob_Quads on 2007-08-17
I don't mount the filesystems in fstab because it was causing problems when the raid arrays stopped working - the machine kept failing to boot or prompting for userinput so I have a script in /etc/rc.local which mounts the filesystems - this means the machine should always boot cleanly

---

