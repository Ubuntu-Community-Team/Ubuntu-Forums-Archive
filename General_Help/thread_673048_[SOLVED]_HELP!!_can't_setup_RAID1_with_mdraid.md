---
title: "[SOLVED] HELP!! can't setup RAID1 with mdraid"
date: 2008-01-20
forum: General Help
---

### Post by inphektion on 2008-01-20
For the life of I can't get a raid 1 going on gutsy.  Never did this before so I could be missing something so here's what I did.  Have alt install 64bit cd.  Have 2 sata drives at /dev/sda and /dev/sdb  
I tried using the text install but after getting wierd errors like it can't write to it or lvm failed etc I've booted to rescue mode and tried command line.  When I run fdisk -l I see both /dev/sda and /dev/sdb have the auto RAID.  I have a /dev/md0 that is configured for RAID1 and contains both /dev/sda and /dev/sdb but from there I'm stuck.
When I boot to the normal installer and try using the guided or manual partitioner on the RAID 1 my only options now are to use /dev/sda or /dev/sdb which must be wrong.

Basically I just want to use the guided part now to setup lvm with /boot and swap space on /dev/md0 so that it writes all that as raid1 to the two /dev/sda and /dev/sdb disks.  But either I kept getting errors about lvm couldn't partition something cause the kernel didn't know about /dev/md0p1 etc. or where I stand now is I only can chose the /dev/sda or /dev/sdb disks not the raid 1 disk...
Is there a straightforward step by step for raid 1.  
All I read is people saying use the alt installer and just configure it but it isn't quite that easy for me.

---

### Post by inphektion on 2008-01-20
hmm... only thing I can think of is I made one large partition in /dev/sda and /dev/sdb.  
then raid1 and now trying to partition the raid /dev/md0 into my /, swap, and /boot.
I think I might need to partition the /dev/sda and /dev/sdb how I want but set each partition to RAID instead of the fs and then make the raid device?  Really counterintuitive but whatever I'll try it.

---

### Post by inphektion on 2008-01-20
ok got it sorted.  (i'm not from london).

I guess it doesn't work as I thought.  I thought I could just take my whole drives, create one large partition as the Auto RAID and then in the md device slice things up.  That wasn't working.
I created / and swap in each sda and sdb then set 2 raids md0 and md1 for the / and swap respectively.  Config'd / as xfs and then moved on.

---

