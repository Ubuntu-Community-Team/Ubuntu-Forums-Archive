---
title: "windows on linux"
date: 2007-07-24
forum: General Help
---

### Post by md5hash on 2007-07-24
is it possible to boot an existing windows os on a separate drive in linux.. 
lets say hda is linux and hdb is windows os.. can load the windows OS while running linux

---

### Post by luisromangz on 2007-07-24
One of my employees tryed to boot an existing phisical Windows XP partition using VMWare server last week, but Windows refused to load. VMWare is able to boot a linux partition as guest using a virtual machine with Windows as host, so in theory it should be possible.

You'll have to download the free (as in beer) VMWare server installer, then create a new virtual machine and thell it to use a phisical partition already existing in your computer's hard drive.

Bye!

---

### Post by dabl on 2007-07-24
> **md5hash said:**
> is it possible to boot an existing windows os on a separate drive in linux.. 
lets say hda is linux and hdb is windows os.. can load the windows OS while running linux

NO, not really.  1 OS at a time, per computer.

However, you can certainly use VMWare Player (free as in beer) and run a VIRTUAL Windows system on your Ubuntu Linux system. This means it is running "in" Linux, or "on" Linux, and it acts like a real Windows machine, except for the hardware connections, which don't actually exist.  Your virtual machine can print, have sound (if Linux isn't using it already), have USB devices connected, have an ethernet connection running, so it's pretty much like a real Windows system.  In fact, you install it with a real Windows installation CD, so you do need that to set it up.

:)

---

### Post by testube_babies on 2007-07-24
It is possible, but (as has been reported) doesn't always work.  Make sure to backup your Windows, just in case:
[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

---

