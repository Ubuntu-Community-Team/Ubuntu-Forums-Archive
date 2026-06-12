---
title: "GParted - unallocated space"
date: 2008-03-21
forum: General Help
---

### Post by Stargazer989 on 2008-03-21
i want to make the unallocated space, actual space i can name and use for baclup.

[[IMG]http://s2.supload.com/thumbs/default/GParted.png[/IMG]](http://s2.supload.com/free/GParted.png/view/)

i already have it all ready in about 20GB partitions, but i can't name the unallocated ones, could someone help ?

please and thank you,

-SG989

---

### Post by wolfen69 on 2008-03-21
you can't name them until you allocate them. unallocated is not considered a partition until you make it something (ext3,fat32,ntfs, etc.)

---

### Post by Stargazer989 on 2008-03-21
yeah... sorry about that, i didn't read the uber confusing help stuff, ive made them into partitions now, all ext3

---

### Post by plucky on 2008-03-21
Stargazer989

You should change the last partition into a logical one as you are only allowed 4 primary partitions on a disk.With a logical partition,you can have a lot more partitions,especially if you want a separate home partition and a swap partition.


See [here](http://www.psychocats.net/ubuntu/partitioning) for partitioning information

Good Luck

---

