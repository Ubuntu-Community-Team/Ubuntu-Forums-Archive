---
title: "Partition"
date: 2008-05-21
forum: General Help
---

### Post by oligray on 2008-05-21
Okay im getting a new pc on friday.. and want to dual boot windows ut primarily use ubuntu

i cnt remember how big the hardrive is but i think its 250GB might be 120 tho

i want a partition for windows.. a partition for ubuntu.. ( do i need a data partition or can this be combined with the ubuntu one)
then a shared fat 32 partition..

how is the best way of doing this..

i will also have partition wizard..

is it a good idea to make these partitions .. i will install windows first and then on ubuntu make the partitions for ubuntu ext3

is this a good way to do it

---

### Post by thisiam on 2008-05-21
get a live cd and make sure everything works fine first, probably will.
under system or preference, on a windows machine right now so cant remember exactly but there you will find Gparted or partition editor. first rezise your windows to whatever you want, second leave the rest unallocated, close gparted.
on the desktop clean install and follow the steps and it will do everything for you, when you get to the partition part select use remaining space, might be phrased different but thats about right. keep following the steps. 
next we can work on getting rid of windows but that will come with time.
about the shared you can use fat 32 or NTFS, you will need [ntfs-3g]("http://www.ntfs-3g.org/")

---

### Post by Nameless_one on 2008-05-21
You can also use ext3 for the shared partition, with [Ext2 IFS for Windows](http://www.fs-driver.org/). The latest version has Unicode support, too :) (although it also has a bug that automatically assigns a drive letter to all your partitions at startup - even the ones you don't want it to).

---

### Post by oligray on 2008-05-21
fat 32 is easier tho..

is it that easy toresize windows..

---

