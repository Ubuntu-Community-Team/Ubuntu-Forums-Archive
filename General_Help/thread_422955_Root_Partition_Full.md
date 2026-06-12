---
title: "Root Partition Full"
date: 2007-04-25
forum: General Help
---

### Post by mole25 on 2007-04-25
The Root partition on my system is full, i have plenty of space on other partitions is there anyway i can add more space to the root partition?

---

### Post by Herman on 2007-04-25
You should download an .iso for the latest [GParted -- LiveCD]("http://gparted.sourceforge.net/") and use that. It's free and it's only around 45 MB to download. The GParted version in the LiveCD is much more advanced than the version we can install in Ubuntu at the moment, 
(I don't know why they are taking so long to give us a more up to date version in Ubuntu. I Guess they have to be pretty carefull everytime they update stuff so maybe it takes a while.)
Anyway, [GParted -- LiveCD]("http://gparted.sourceforge.net/") can move Linux partitions and resize them from either the beginning of the partition or the end of it.
You might also right-click on your partition that is too full first and click 'check', for [GParted -- LiveCD]("http://gparted.sourceforge.net/") to run a filesystem check on it. A filesystem check is always a good thing to do, and one of hte features built into the [GParted -- LiveCD]("http://gparted.sourceforge.net/") filesystem checks is that they also check that the filesystem is the right size for the partition it's in for you. I have had it happen to me before that the filesystem is full, but the filesystem is not filling the whole partition. After running that with [GParted -- LiveCD]("http://gparted.sourceforge.net/") you might find you don't even really need to resize. Try that first.

Regards, Herman :)

---

