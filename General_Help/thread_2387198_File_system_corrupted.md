---
title: "File system corrupted"
date: 2018-03-16
forum: General Help
---

### Post by sofasurfer on 2018-03-16
Ubuntu 16.04.
Partition residing near end of disk. I used Gparted to attempt to resize bigger. Halfway through it failed and now I have an inaccessible file system. Is this a gauranteed loss or can I learn to fix it. 
Point me in a direction please

---

### Post by oldos2er on 2018-03-16
How exactly did it fail? Did you save the 'Details' of the error? Without knowing that it's difficult to diagnose.

---

### Post by sofasurfer on 2018-03-17
I did not save the details. Is there any way to salvage this? Didn't know this would go bad.

---

### Post by #&amp;thj^% on 2018-03-17
So sorry to hear this, :( brings back some very painful but well learned memory's
This is what to consider before you change partition size:

Changing partition size always bears a risk of data loss. Therefore backup all valuable data.

Only partitions that are unmounted can be altered, eg;>> work on a live session (boot Ubuntu "Try First").

I've had this happen twice now (About 10 years ago) and it's seared painfully in my mind - it turns a 2 second operation into hours of data shifting and increases the risk of further problems. It'd be a serious pain to move back.

TestDisk and Photorec might help recovering your needed data.
[https://www.cgsecurity.org/wiki/PhotoRec](https://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by sofasurfer on 2018-03-27
I am going to have to learn some of this stuff from scratch before I can even grasp what needs fixing.
Question: When I move a partition on a drive from one location to another, is the partition table really what I am changing or am I actually moving all of the data thats on the drive? If this is the case then what I really need to do is rebuild the partition table. Is this the case?

---

