---
title: "Wanting to format my External Hard Drive. Advice?"
date: 2006-09-13
forum: General Help
---

### Post by Grog140 on 2006-09-13
I want to  format my external Hard Drive to a different format. What is the best way to do it under Ubuntu?

I want to format it to Ext3.

Thanks.

---

### Post by monktbd on 2006-09-13
i partitioned my external harddisk the following way:

30 GB fat32 if i ever need to exchange a bigger amount of data with a windows machine.
220 GB ext3 as my backup and data partition.

think of what you want to do with it and fit the partitioning and the filesystem to those needs.

best way under ubuntu is probably gparted (gnome partition editor).

---

### Post by coffeecat on 2006-09-13
Either: Boot from the live CD and use Gparted (System > Administration > Gnome Partition Editor)

or

Use Synaptic to install Gparted to your hard disk install and then find it in the same place.

Well - I'm assuming you're using Ubuntu here; you don't say. If you're using Kubuntu the KDE equivalent is Qtparted. It will do the job just as well.

One point. The parteds won't let you reformat a mounted partition, and the USB disk will be automatically mounted as soon as you plug it in. Either 'umount' from the terminal or right-click and 'eject' from the GUI.

---

