---
title: "swap partition"
date: 2007-04-09
forum: General Help
---

### Post by finita on 2007-04-09
Hi,

I'm new in linux world. Recently I decided to move to linux and after some research decided on Ubuntu.
Now using 6.06.
I have a question:
I have 512 MB of swap partition. I want to install Oracle and it required at least 1024 MB swap space.
How can I increase this partition without repartitioning, without using partition magick or other tools?
Is there any command to repartition this?
Could you please tell me alternative ways to repartition swap?

Thanks

---

### Post by mikewhatever on 2007-04-09
Gparted live cd [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
You should shrink one of the adjacent partitions to create unallocated space, then enlarge the swap.

---

### Post by bernied on 2007-04-09
You will need to use some partitioning tool.
The popular choice round here seems to be gparted, which comes as a live-cd as an added bonus. Other variants are parted (text-based) and qtparted.

You might also make do with just fdisk, though this will only create or remove partitions, not resize, so you might have to remove the swap and a neighbour, then recreate both of them different sizes. Removing a partition might makes its data inaccessible.

I believe that it is generally considered a bad idea to try to resize a partition on a disk that you are using at the time, this means that you should probably do stuff like this from a live cd.

If you give the output to:
```
sudo fdisk -l
```
someone here might be able to help some more...

---

