---
title: "Partitioning utility"
date: 2007-02-06
forum: General Help
---

### Post by pagady13 on 2007-02-06
Hi,

What **partitioning utility** am I supposed to use in Ubuntu?

Thanks!

---

### Post by wieman01 on 2007-02-06
"gparted" aka "Gnome Partition Editor". I think it is installed by default, if not you'll find it in the repositories.

---

### Post by pagady13 on 2007-02-06
Thank you !

---

### Post by Bartender on 2007-02-06
Generally speaking, you'll get more reliable results if you download [GPLCD]("http://gparted.sourceforge.net/livecd.php") and make a bootable CD than if you use the Ubuntu LiveCD to access Gnome Partitioner in Administration.

You can also get to the partitioner on the LiveCD by starting to go thru an install.  After using the partitioner, you can just abort the install if you wish.

---

### Post by Sef on 2007-02-06
> Generally speaking, you'll get more reliable results if you download GPLCD and make a bootable CD than if you use the Ubuntu LiveCD to access Gnome Partitioner in Administration.


That's because GParted from its site is newer than the one in Ubuntu.

---

### Post by bodhi.zazen on 2007-02-06
gparted is on the live CD, but is not installed by default.

You can use cfdisk from the CLI if you like, it is easy to use

How to: [http://www.linux.org/docs/ldp/howto/IBM7248-HOWTO/cfdisk.html](http://www.linux.org/docs/ldp/howto/IBM7248-HOWTO/cfdisk.html)

cfdisk will not resize or format a partition. Again you can format from the CLI, see here:

[http://www.ubuntuforums.org/showthread.php?t=282018](http://www.ubuntuforums.org/showthread.php?t=282018)

As suggested by Bartender, it is best to manage partitions from a live CD. The gparted live cd is very nice and has some additional tools as well. It is worth the download and burn.

You can resize and format partitions from gparted, either on the Ubuntu desktop CD or gparted ...

HTH

---

### Post by laidback on 2007-02-06
Very much agree. Download Gparted Live CD ISO, not a lot of effort; well worthwhile.
Remember that you cannot repartition a partition that is mounted. Gparted live CD allows you to manage your hdd partitions, resizing, erasing, creating new etc.

---

