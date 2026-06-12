---
title: "Why? During Creation of RAID5, watch cat /proc/mdstat shows &quot;recovery&quot;"
date: 2013-04-14
forum: General Help
---

### Post by agentofcode on 2013-04-14
**Preliminary**
I am following this tutorial on [setting up a software RAID5]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm"). Drives are brand new and have passed testing.

**Concern**
During the creation phase of the RAID I am receiving the following output.

**watch cat /proc/mdstat** Results:
> Every 2.0s: cat /proc/mdstat                                                               Sun Apr 14 04:23:57 2013
 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sde1[4] sdd1[2] sdc1[1] sdb1[0]
      5860133376 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [UUU_]
      [=>...................]  recovery =  6.5% (127507428/1953377792) finish=286.3min speed=106288K/sec
 
unused devices: <none>

Why would I see "recovery" and "[4/3] [UUU_]" as part of the status of this RAID5 creation? Is this something I should be concerned about?

---

### Post by rubylaser on 2013-04-14
This is perfectly normal :) Recovery is exactly what it should say until your array is done syncing. Once all your disks are in sync that will no longer show as recovering.

---

### Post by agentofcode on 2013-04-14
Just wanted to be sure since it was technically "creation" of the RAID and not an actual recovery of anything on my part. I suppose that is just how the status reads regardless of creation or actual recovery.

Thanks!

---

