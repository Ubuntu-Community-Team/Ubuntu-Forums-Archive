---
title: "Ubuntu on SSD with LVM."
date: 2016-04-28
forum: General Help
---

### Post by stepheny on 2016-04-28
I recently bought a 480GiB SSD drive. I formated it into a swap partition and an Ext4 partition and then installed Ubuntu 15.10 from a CD (and internet). I ticked the box LVM during the installation as I couldn't see any disadvantages to using LVM. The install went fine and the SSD is working even better than I expected. 

Having done some reading up on using SSD's I decided to implement Autotrim but then discovered that according to GParted my Ubuntu installation is on an Ext2 virtual partition (/dev/sda2, 446.89GiB)) inside an lvm2 pv partition (/dev/sda5, also 446.89GiB). My swap partition has been removed and in its place a /boot partition (/dev/sda1, 243MiB - 143MiB used) using Ext2 has been created. The /boot partition is not inside the lvm partition. Gparted doesn't give any idea how much of the partition /dev/sda2 is being used.

I have never used LVM before and am worried that I have not installed Ubuntu on the SSD in the best possible way. Could someone offer any advice? I am prepared to do another install, but as I said the installation is working very well for the time being.

---

### Post by oldfred on 2016-04-28
That is a standard LVM full drive install.
LVM is logical partitions inside the physical partition. But the boot partition is normally outside the LVM.

Since you are using Logical partitions, you cannot use gparted on those inside the physical partitions. You have to use LVM tools.

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

---

### Post by Dennis N on 2016-04-28
Don't panic. The LVM setup is good. There are tools to handle everything, and they are already on your system. Gparted cannot do much except see that a partition is being used for LVM. Best thing to do is read this introductory guide on LVM on Ubuntu. It's where I started learning about it. As you will see, LVM makes a lot of things easy to do.

[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

---

