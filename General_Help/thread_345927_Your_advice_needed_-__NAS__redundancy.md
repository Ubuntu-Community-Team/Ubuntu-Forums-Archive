---
title: "Your advice needed -  NAS / redundancy"
date: 2007-01-24
forum: General Help
---

### Post by shickey on 2007-01-24
Hello all,

I'm trying to figure out a solution to my problem.

I have roughly 100GB of data between mp3s, pics, web content, and other data.

I currently run ubuntu on my server (800 MHz) and it shares my data via samba (very small OS drive, 120 GB data drive).  I have a client PC running windows xp that I mainly use for PC gaming and Xbox360 media content serving.

I have the following hardware, and am looking to use as much as possible to create a NAS / file/web server.  I'd really hate to spend more money on hardware...when all of this will go to waste.

For Hard Drives, I'm still all IDE.
Recently purchased PCI IDE Card (presumably for adding additional drives to the server)
7.6 GB (ubuntu server OS drive)

1 x 160 GB
1 x 120 GB 
1 x 80 GB
1 x 60 GB 
afore mentioned 7.6 GB OS drive

I'd really like to implement RAID, but I'm not sure if that is possible, given my different sized drives.

Thanks for the help!
:guitar:

---

### Post by shickey on 2007-01-24
Oh, I should mention that I'm an experienced Unix administrator professionally, and am very comfortable with LVM, and other possibilities, I just don't know how to put my hardware together to properly form a solution.

Thanks again.

---

### Post by shickey on 2007-01-25
Anyone have any ideas?

---

### Post by kosmic on 2007-01-25
Yes it is possible, with LVM and RAID. I will explain here later (in about 1 or 2 hours) im going to work right now.

You have a dificult setup to acomplish because if you Want RAID 1 you have to had the same space for replication. 

so have a look where if you become stuck just post here your troubles - [http://penguinsecurity.net/wiki/index.php?title=Managing_Disk_Space_with_LVM](http://penguinsecurity.net/wiki/index.php?title=Managing_Disk_Space_with_LVM)


A solution is to partition the 160GB disk so it can only use 120GB and the 80GB disk to 60GB.

---

