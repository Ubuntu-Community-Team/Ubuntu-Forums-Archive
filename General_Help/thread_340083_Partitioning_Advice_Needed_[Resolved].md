---
title: "Partitioning Advice Needed [Resolved]"
date: 2007-01-16
forum: General Help
---

### Post by dillzz on 2007-01-16
Hopefully I can word this correctly for you guys.  

Currently I have a 40GB drive split into two partitions.  

XP 20GB
/dev/hda1

Ubuntu 20GB (Active Partition with Grub)
/dev/hda2

I want to install Mac OSX to the same hard drive and cannot resize the Ubuntu partition, leaving me with a choice of resizing the XP partition.  This is where I am looking for advice.  Being that I resize/repartition to the following scheme:

XP 10GB    
/dev/hda1  

OSX 10GB       
/dev/hda?       

Ubuntu 20GB (Active Partition with Grub)
/dev/hda?

Will my Ubuntu partition still be /dev/hda2, or /dev/hda3, if it does get moved logically to /dev/hda3 - changing Grub to point to hd0,2 instead of hd0,1 is all I need to change I assume.   I cannot mess this machine up and I know if all else fails XP will still boot which is what I really don't want to happen!

Thank You...

---

### Post by bodhi.zazen on 2007-01-16
1. You should be able to resize your ubuntu partition, but you should do so from a live CD, either the ubuntu desktop or gparted CD.

2. I thing if you partition as you propose your partition numbering will change.

You would then need to edit or re-install grub and edit fstab.

You should know how to do these things before you change your partitions or install OSX.

---

### Post by dillzz on 2007-01-17
Update:

As it turns out I have succesfully partitioned and got everything working.  The Ubuntu partition changed to /dev/hda3 and I only had to change grub/fstab.  I did run into a grub 17 error upon reboot.  I solved this by simply reinstalling grub to the root of hda3 through a live disc and all is well...Thanks for the help.

---

