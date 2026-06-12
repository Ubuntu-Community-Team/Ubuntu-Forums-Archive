---
title: "I can't use space of the system partition"
date: 2014-07-24
forum: General Help
---

### Post by tassadar2 on 2014-07-24
Hi all,

I've a problem with a computer that runs with kubuntu 14.04, the question is it has a 2 terabytes system disk, whose installation came from a 120gb SSD via cloning with clonezilla and resizing partitions automatically (I told this because perhaps can be important, perhaps not).

[IMG]http://i62.tinypic.com/141mhbb.jpg[/IMG]

/dev/sda1 has 1,76 TiB, but it says that 1,65 TiB are unassigned, so I can't use the space. I have try to resize partition but gparted doesn't allow me to.

As you can see on picture, if I go to properties of partition it shows a warning message saying something like:

**"Warning: 1.65 TiB of unassigned space on partition, to make filesystem grow in order to fill the partition, select partition and choose "Partition --> Check" from the menu"**

I'm unable to, since this option doesn't appears.

My question is: How can I repair it so I can use all the space? If possible, I want to do it from the kubuntu installation, since I'm not phisically on the computer and only can connect remotely.

Many thanks in advance

---

### Post by oldfred on 2014-07-24
You cannot use gparted from your working system. Little lock symbols mean it is mounted.
Try again with Ubuntu live DVD or flash drive or a gparted liveCD. You may still have to click on swap and swap off to unmount swap.

Must better with very large TB sized drives to have 20 or 25GB / (root) partition so drive does not have to scan entire 2TB to find system files. And then use rest of drive as /home or just as data partition(s).

---

