---
title: "Need help getting VirtualBox to work"
date: 2008-06-18
forum: General Help
---

### Post by MR.UNOWEN on 2008-06-18
After some updates, VB is not working. Also (since the beginning) I couldn't get it to see any of my drives (both USB and internal HD). Can some one help me fix these problems....

Here's the error:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by NetworkGuy on 2008-06-18
Type this from the terminal   > sudo aptitude install virtualbox-ose-modules-generic

PS..  If you are running the latest kernel, you may have to wait a couple of days for the correct module for the latest kernel to become available.

Sorry, I can't help with the USB and hard drives.

---

### Post by MR.UNOWEN on 2008-06-18
Thanks that did the job. By the way if I make a copy of the partition, will I be able to return the partition to its former state by pasting over the partition with the copy?

Does anyone know how to make VB see all my storage devices?????

---

