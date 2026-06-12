---
title: "Manually getting packages"
date: 2007-02-09
forum: General Help
---

### Post by Hawkeye05 on 2007-02-09
I've installed Ubuntu Edgy on my Desktop, and I need packages, Build-essential, stuff to get netzero and wine to work.  but i have dialup and i cant figure out how to launch netzero since ive installed it with the .deb.  I have limited to high speed at school and through my PDA, i've tried [http://packages.ubuntu.com/](http://packages.ubuntu.com/) hbut that seems to be a never ending circle of death.  i just need all the files included in the packages when you get them through synaptic.  PLEASE HELP!!!

---

### Post by gradedcheese on 2007-02-10
No, you should really install the packages (so that you can cleanly upgrade/uninstall/etc).  To do it, use that website, download the package(s) you need, including all their dependencies that you don't already have, and then take them home on a CD or USB disk or something.  Then use:

sudo dpkg -i /path/to/packages/*.deb

to install them all.  For example, your USB disk might be /media/usbdisk

---

