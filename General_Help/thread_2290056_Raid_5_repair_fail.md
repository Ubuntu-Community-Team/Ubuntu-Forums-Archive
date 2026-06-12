---
title: "Raid 5 repair fail"
date: 2015-08-09
forum: General Help
---

### Post by jason.doughty.jtg on 2015-08-09
one of my HDD died /dev/sda1 which was part of my raid 5, the OS ubuntu  is on a different HDD not part of the raid. I add the new HDD the  started to repair the raid.I check back a few hour later and it has stop  repairing, so I rebooted and entered the follow command:

sudo mdadm --stop /dev/md0
mdadm: stopped /dev/md0
:~$ sudo mdadm --assemble /dev/md0 --scan --force
mdadm: forcing event count in /dev/sde1(3) from 24483 upto 24487
mdadm: clearing FAULTY flag for device 3 in /dev/md0 for /dev/sde1
mdadm: Marking array /dev/md0 as 'clean'
mdadm: /dev/md0 has been started with 8 drives (out of 9) and 1 spare.
:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[1] sda1[9] sdj1[5] sdi1[6] sdh1[7] sdg1[8] sdf1[4] sde1[3] sdc1[2]
      15627058112 blocks super 1.2 level 5, 4k chunk, algorithm 2 [9/8] [_UUUUUUUU]
      [>....................]  recovery =  0.0% (428160/1953382264) finish=1368.3min speed=23786K/sec


cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[1] sda1[9](S) sdj1[5] sdi1[6] sdh1[7] sdg1[8] sdf1[4] sde1[3](F) sdc1[2]
      15627058112 blocks super 1.2 level 5, 4k chunk, algorithm 2 [9/7] [_UU_UUUUU]

I check the health of /dev/sde1 and it has 1000 bad sector, dose this mean I lose all of the data?
What can I do to fix my raid?

---

