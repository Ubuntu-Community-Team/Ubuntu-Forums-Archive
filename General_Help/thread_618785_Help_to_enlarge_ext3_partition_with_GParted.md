---
title: "Help to enlarge ext3 partition with GParted"
date: 2007-11-20
forum: General Help
---

### Post by climbingrose on 2007-11-20
Hi guys,

My current partitions are as in the screenshot. What I want to do now is to enlarge /dev/sda2 to take up the unallocated space (18.24GB, before /dev/sda7). I know that I have to reboot to a live CD but I just want to know what is the strategy to increase space on /dev/sda2. Thanks.

---

### Post by bodhi.zazen on 2007-11-20
Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

The key will be which version of gparted you use. Either download the gparted live CD or use a gutsy live CD.

---

### Post by climbingrose on 2007-11-20
I did read the documentation before posting this question. The problem is that the partition I want to resize (/dev/sda2) is before the extended partition (/dev/sda3) which contains the unallocated area. I now I want to reassign this unallocated area to sda2. I'm aware that I can only enlarge a partition if the unallocated area sits next to it. How do I do that in my case because the extended partition (sda3) is the one next to the one that I intend to resize. Thanks.

---

### Post by bodhi.zazen on 2007-11-21
Oh, ok, sorry then.

You need to move your partitions. This is a nice walk through :

[http://gparted.sourceforge.net/larry/move/move.htm](http://gparted.sourceforge.net/larry/move/move.htm)

You can use the copy-paste function ...

If all else fails ...

copy the sda2 -> unallocated

resize

delete the sda2

move the other partitions

move new "sda2"

You need to be p repaired to manually re-configure grub and /etc/fstab

---

