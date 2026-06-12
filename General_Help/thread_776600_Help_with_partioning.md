---
title: "Help with partioning"
date: 2008-04-30
forum: General Help
---

### Post by peaboy787 on 2008-04-30
Hey guys i need ur help on this one
You see im trying to Install Linux From Scratch(LFS) and need a new partition i already have 3 partitions but i have an 8 gig unallocated space that i want to use for LFS umm i was thinking of moving the space to the extended partition but cant see how to do it

Is it ok to make the LFS partition inside that extended partition and how would i move the space there i put a pic in so u guys can see what im talking about

and i cant right-click resize/move the 8 gigs its grayed out

[IMG]http://i152.photobucket.com/albums/s188/peaboy787/Screenshot.png[/IMG]

---

### Post by garyedwardjohnston on 2008-04-30
Not sure what u r doing with so many partitions.

Can u not format it?

---

### Post by logos34 on 2008-04-30
You can't move unallocated space. 

The only solution is to delete the extended partition and swap (sda4 & 5), then make a new extended out of the unallocated space and place LFS root and swap inside on logical partitions.  Make sure to edit swap line in ubuntu's /etc/fstab file.

---

### Post by louieb on 2008-04-30
You can move sda3 into the unused space. then your unused space will be between sda3 and sda4. Go to a movie this this will take a few hours.

then grow your extended partition to the left. Now the unused space will be in the extended partition. and you can use it to add the logical partition for LFS.

---

### Post by peaboy787 on 2008-05-01
Thx Logos, i did what u said and everything fit well into place

:KS:):):guitar::):):KS

---

