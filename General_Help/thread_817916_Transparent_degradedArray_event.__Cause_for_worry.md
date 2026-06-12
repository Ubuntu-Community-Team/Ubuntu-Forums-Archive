---
title: "Transparent degradedArray event.  Cause for worry?"
date: 2008-06-04
forum: General Help
---

### Post by r3by on 2008-06-04
a week ago there was a degradedArray event on my software raid 5 array.  I didn't notice it at the time and it rebuilt itself immediately and transparently, but then I noticed this message from mdadm.


```
From: mdadm monitoring <root@ibm>
Subject: DegradedArray event on /dev/md1:ibm
Message-Id: <E1Jpq4k-0001lr-Pl@ibm>
Date: Sat, 26 Apr 2008 12:28:46 -0700

This is an automatically generated mail message from mdadm
running on ibm

A DegradedArray event had been detected on md device /dev/md1.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdc2[3] sdb2[1] sda3[0]
      390620288 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]
      [>....................]  recovery =  0.0% (1160/195310144) finish=2712.6min speed=1160K/sec
      
md0 : active raid5 sda2[0] sdc1[2] sdb1[1]
      388692480 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>
```

I was playing music off md1 the whole time and there wasn't even a skip, but this seems like something that shouldn't happen, and I have a lot of irreplaceable data on those arrays.  Should I be worried?  Is this an ominous sign, or something benign and routine?

I remember that I did a recursive chmod around that time of all the files in 2 400GB software arrays (simultaneously).  That must be what set it off.  The drives are less than a year old.  

I'd be thankful (and would sleep better) if someone could explain this and/or suggest a course of action (or inaction).

---

### Post by fjgaude on 2008-06-04
I'm not much help here... how long did it take for the resync to occur?

These kind of things happen when there been a read/write error of a drive and checksums don't match... the resync starts.

What does this show:

```
sudo mdadm -D /dev/md1
```

It's hard to say if your recursive command had anything to do with it.

---

### Post by r3by on 2008-06-04
```

mdadm -D /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Sat Apr 26 12:28:41 2008
     Raid Level : raid5
     Array Size : 390620288 (372.52 GiB 400.00 GB)
  Used Dev Size : 195310144 (186.26 GiB 200.00 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Wed Jun  4 05:46:32 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 88414c40:0fe22156:4e7aacd3:b438a8f1 (local to host ibm)
         Events : 0.22

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       18        1      active sync   /dev/sdb2
       2       8       34        2      active sync   /dev/sdc2
```


> how long did it take for the resync to occur?
Around an hour I think, and then the other one, /dev/md0 did a resync.

> These kind of things happen when there been a read/write error of a drive and checksums don't match... the resync starts.
Thanks.  Good to know that that's not real unusual.  A little disturbing that I'm getting rear/write errors for no particular reason, but I guess that's why I have parity and a journaling filesystem.

---

### Post by fjgaude on 2008-06-04
When I wished to increase the number of drives in an array I used this command:

```
sudo mdadm --grow /dev/md1 -n=4
```

Seems that -D thinks you only have an -n=3 array.

Good luck... I've had nothing but that with my raid5, the same one running for nearly two years now, with 300GB Seagate drives. I did have a failure sometime back but recovered just fine.

---

