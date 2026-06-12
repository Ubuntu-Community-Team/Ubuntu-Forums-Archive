---
title: "PLEASE HELP ! - Virtual Box -"
date: 2008-05-04
forum: General Help
---

### Post by Rob2008 on 2008-05-04
I installed virtual box,to run xp which worked really well but all of a sudden i tried to start my xp and got this error:-


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}



PLEASE someone help i need to get it working again :(


regards


Rob

---

### Post by KrazyPenguin on 2008-05-04
Did you upgrade your kernel???

If so, try using the older one during boot, and see if that helps.

I'm not sure, your could try this:

 sudo /etc/init.d/vboxdrv setup

or search synaptic for that package it wants.

Good luck!!
;-)

---

### Post by charonn0 on 2008-05-04
This might be what you're looking for: [http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)

---

