---
title: "issues with GParted partition tool"
date: 2016-03-13
forum: General Help
---

### Post by bijaydeyp on 2016-03-13
I recently re-installed trusty 14.4.4 lts on dual-booted(with Windows 7) samsung HDD. during some partition editing I noticed that on 'create new partition' wizard in the box of "free space preceding" the minimum no of MBs are always 1 inatead of Zero. it means if I create four logical partition I waste total 4 MBs unallocated disk space!!


did anyone face the same issue? or has it a bug? plz tell me.

---

### Post by howefield on 2016-03-13
Possibly this post..

[http://ubuntuforums.org/showthread.php?t=1568720&p=9813305&viewfull=1#post9813305](http://ubuntuforums.org/showthread.php?t=1568720&p=9813305&viewfull=1#post9813305)

---

### Post by oldfred on 2016-03-13
And this which is from same author as howefield's link.
 Partition does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

---

### Post by bijaydeyp on 2016-03-15
now it's all clear. thanks guys.

---

