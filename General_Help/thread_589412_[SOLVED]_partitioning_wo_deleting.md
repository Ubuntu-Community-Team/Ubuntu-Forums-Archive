---
title: "[SOLVED] partitioning w/o deleting"
date: 2007-10-24
forum: General Help
---

### Post by tpettit on 2007-10-24
Hi ! I installed ubuntu in one single partition which uses the entire hard drive, and would like to install win XP too, on the same hard drive. Will the ubuntu partitioner on the installation disk delete my files if I resize the existing partition and create a new one?
and if so, what can I use in order to create a new partition without deleting my files?

Thank you !

---

### Post by indytim on 2007-10-24
I would recommend that you download and burn a copy of GParted Live.  After the iso has been burned to a CD, boot to it and resize your Ubuntu partition.  With the newly created unallocated space, create the NTFS partition for your Windows ops.  Obviously, at boot to Windows install, you will need to tell Windows where to go :):).

Here's the link for GParted:
[http://gparted.sourceforge.net/index.php]("http://gparted.sourceforge.net/index.php")

IndyTim

---

### Post by forestpixie on 2007-10-24
I use [gparted]("http://gparted.sourceforge.net/download.php") livecd to do my partitioning - you can resize using that it'll be quicker, burn it as an iso and boot with it - you won't have to wait for the ubuntu disc to load. But there is a partitioner on the live cd - the version on Feisty is quite old, but Gutsy has a newer version. Believe it's in the system > admin menu on the live cd.

Once you've got your partition install xp, although I think it likes to be first, installing xp will lose your grub menu when it greedily uses it's own boot.

To fix grub after the xp install either download and burn [supergrub]("http://supergrub.forjamari.linex.org/?section=download") and boot with that or there are methods to sort grub with the ubuntu livecd

fixing grub - [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
recover after windows - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by tpettit on 2007-10-24
awsome! thank you both!

---

### Post by forestpixie on 2007-10-24
that's no problem - mark the thread solved :) - and see you on the other side

---

