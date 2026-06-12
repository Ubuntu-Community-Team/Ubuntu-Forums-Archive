---
title: "Why did Ubuntu 15.10 install itself onto an Ext2 logical partition?"
date: 2016-04-27
forum: General Help
---

### Post by stepheny on 2016-04-27
I recently bought a SSD drive. I formated it into a swap partition and an Ext4 partition and then installed Ubuntu 15.10 from a CD (and internet). I ticked the box LVM during the installation as I couldn't see any disadvantages to using LVM.  The install went fine and the SSD is working even better than I expected. 

Having done some reading up on using SSD's I decided to implement Autotrim but I have discovered that my Ubuntu instalation is on a Ext2 virtual partition (/dev/sda2) inside an lvm2 pv partition (/dev/sda1). My swap partition has been removed and in its place a /boot partition on Ext2 has been created. The /boot partition is not inside the lvm partition.

I am not overly concerned as I can easile run ```
sudo fstrim /
``` in a cron job, but would appreciate knowing why the Ubuntu OS installed itself in this way.

---

### Post by dino99 on 2016-04-27
you now can choose ext4 on recent ssd; but previuosly it was on ext2 (so the default setting)
to set you choice, you need to select the 'manual' install way, instead of letting the installer doing the default way.

[http://ubuntuforums.org/showthread.php?t=2276792](http://ubuntuforums.org/showthread.php?t=2276792)
[https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)

---

