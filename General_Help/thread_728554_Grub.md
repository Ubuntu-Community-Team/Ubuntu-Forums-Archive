---
title: "Grub"
date: 2008-03-18
forum: General Help
---

### Post by hgiahjd on 2008-03-18
Hi
My experience with linux in the past was that if I lost the ability to boot Linux, I would re-install.  At this time I have Ubuntu 7.10 on a laptop and a desktop and have upgraded regularly and it is getting to the point where re-installing is not attractive (D/L limits, data etc)
I have learned the hard way how to recover from failed installs of other versions/distros which over-write the MBR

Reboot from live disk (version doesn't matter) 
Open a terminal and
sudo grub
then 
Find /boot/rub/Stage1
this will result in the designation of partition holding the operating system
something like
(hd0,0) OR (hd0,5) OR both if you have 2 installs of linux
use the one that relates to the partition you wish to boot and issue the command
root (hd0,5) or whatever applies to your circumstances
and
setup (hd0)

that should do it
This assumes one hdd and Grub installing to hda/(hd0)
Good Luck
Enjoy

---

### Post by nick_h on 2008-03-19
The thread [How to install Grub from a live Ubuntu cd.](http://ubuntuforums.org/showthread.php?t=224351) is also worth reading.

---

