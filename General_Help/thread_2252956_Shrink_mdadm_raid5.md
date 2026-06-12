---
title: "Shrink mdadm raid5"
date: 2014-11-16
forum: General Help
---

### Post by marcus3 on 2014-11-16
Summary: I'm trying to migrate my existing 8-disk RAID5 array to an 8-disk RAID6, but I'm getting errors I don't understand as I try to '--grow' the array from RAID5 8 disks to RAID5 7 + 1 hot spare.

The array is a set of 8 1TB disks. 

I don't have a complete backup (the array was constructed from parts I had lying around and some cheap second hand disks, and just stores movie rips), and I'm not going to buy extra storage just for this process. Hence I can't just wipe the array and start from scratch (the manual suggests this migration should be easy, if I had known it was this much trouble I would have just stuck with RAID5).

My method is the same as both [this forum post]("http://ubuntuforums.org/showthread.php?t=1794121&p=11000041#post11000041") and [this blog]("http://blog.stalkr.net/2009/10/reducing-number-of-devices-in-raid-5.html").

Successful steps I've taken so far:
[LIST=1]
[*]unmounted, fscked 
[*]Shrunk the LVM physical volume that was on the array to 5GB 
[*]Shrunk the RAID array by ```
mdadm /dev/md126 --grow --array-size=5594194903
``` 
[/LIST]

At this point, the array seems correct:
```
root@computer:~# mdadm --detail /dev/md126
/dev/md126:
        Version : 1.2
  Creation Time : Mon Oct  6 17:46:38 2014
     Raid Level : raid5
     Array Size : 5594194903 (5335.04 GiB 5728.46 GB)
  Used Dev Size : 976629248 (931.39 GiB 1000.07 GB)
   Raid Devices : 8
  Total Devices : 8
    Persistence : Superblock is persistent

    Update Time : Sun Nov 16 18:46:56 2014
          State : clean 
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : computer:oneTBraid5  (local to host computer)
           UUID : 6ebb0e87:98e68e9c:26b1e1c9:4a1e9edd
         Events : 38901

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       33        1      active sync   /dev/sdc1
       2       8       81        2      active sync   /dev/sdf1
       9       8      129        3      active sync   /dev/sdi1
       6       8       65        4      active sync   /dev/sde1
       5       8       49        5      active sync   /dev/sdd1
       7       8      177        6      active sync   /dev/sdl1
       8       8       17        7      active sync   /dev/sdb1
```


Now when I try change the array from 8 disks to 7 + 1 hot spare using: ```
root@computer:~# mdadm /dev/md126 --grow --raid-devices=7 --backup-file=/home/marcus/mdadm.backup
mdadm: Cannot set device shape for /dev/md126: Invalid argument
root@computer:~# dmesg | tail
md: couldn't update array info. -22
```

Since it complains about the shape argument, I tried ```
root@computer:~# mdadm --grow /dev/md126 --raid-devices=7 --level=5 --backup-file=/home/marcus/mdadm.backup
``` but it gave the same error.

Trying to migrate directly to RAID6 (from 8 disk and no hot-spare RAID5):
```
root@computer:~# mdadm /dev/md126 --grow --level=6 --backup-file=/home/marcus/mdadm.backup
mdadm: Need 1 spare to avoid degraded array, and only have 0.
```

I tried ```
root@computer:~# mdadm --grow /dev/md126 --raid-devices=7 --spare-devices=1 --backup-file=/home/marcus/mdadm.backup
mdadm: :option --spare-devices not valid in grow mode
```
despite the manual stating that --spare-devices works for --grow.

I checked and I don't have a write-intent bitmap set on this array:
```
root@computer:~# mdadm -G /dev/md126 --bitmap=none
mdadm: no bitmap found on /dev/md126
```

Some details about my system: 
[LIST]
[*]kernel 3.16.0-24-generic, 
[*]Ubuntu 14.10 full desktop install, 
[*]mdadm - v3.3 - 3rd September 2013 
[/LIST]
 
What's going wrong? What is the invalid shape argument in the command?

---

