---
title: "[SOLVED] /var/run and /var/lock take up 1gb each??"
date: 2007-09-12
forum: General Help
---

### Post by hamster_billy on 2007-09-12
I was running short on hard disk space, and was looking round to see what was using it all, when I found /var/run and /var/lock, which have 2gb unusable space between them, for 7.3kb of actual data. I was hoping someone could enlighten me about why these folders take up so much space.

The published miniumum requirement for an ubuntu install (not on a low-spec computer) is ~2gb hard disk ([https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)), with a recommended minimum of 8gb. This makes me suspect that taking up 2gb just for these two folders may not be standard.

Is it safe to reduce the size of /var/run and /var/lock to something more similar to the size of their contents? And if so, how do I do it?

---

### Post by hamster_billy on 2007-09-12
By running df, I've just found I have a total of five folders of size 1gb for small amounts of data. I'd seen that for my linux partition 'used' + 'available' was around 2gb short of the partition size, and thought when i found /var/run and /var/lock that they were to blame. Adding up the numbers though gives 1.6gb lost space, so there must be another explanation.

> Filesystem...1K-blocks......Used..........Available......Use%..Mounted on
/dev/sda5..........30866236..17441600..11856696...60%....../
varrun.................1019300........116..........1019184.....1%....../var/run
varlock................1019300..........0............1019300.....0%....../var/lock
udev....................1019300........144..........1019156.....1%....../dev
devshm...............1019300.......... 0............1019300.....0%...../dev/shm
lrm.......................1019300.......33788........985512.....4%....../lib/modules/2.6.20-16-generic/volatile
/dev/sda2...........24659768...20678676...3981092...84%....../media/Windows
/dev/sda1...........20249900...13058984...7190916...65%....../media/Media

Can someone enlighten me as to whether these folders may have something to do with my lost 1.6gb?

---

### Post by psusi on 2007-09-12
df reports the total and used space on each filesystem ( partition ).  /var/run and /var/lock are on tmpfs, which means the files there are stored in ram or swap.  The maximum size of those filesystems is 2 GB; they are not using anything on disk.

---

### Post by hamster_billy on 2007-09-12
I find that encouraging. Thanks.

---

