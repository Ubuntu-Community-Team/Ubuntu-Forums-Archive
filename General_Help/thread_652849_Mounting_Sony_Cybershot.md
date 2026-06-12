---
title: "Mounting Sony Cybershot"
date: 2007-12-29
forum: General Help
---

### Post by koskos on 2007-12-29
I'm trying to connect my Sony Cybershot DSC-W55 (as a memory stick) but when I plug in the USB cable it says "USB Mode Connecting" on the camera and Ubuntu does not actually mount it.

What should I do to mount it?

---

### Post by phidia on 2007-12-29
If you open a shell/terminal and type dmesg | tail you will get some output there about the camera. You can search that output string or post it here. 
Many USB cameras are supported but some need extra tweaking to mount.

---

### Post by koskos on 2007-12-29
I got:

> [  841.616000] usb 5-5.4: new high speed USB device using ehci_hcd and address 5
[  841.708000] usb 5-5.4: configuration #1 chosen from 2 choices


---

### Post by whos2know on 2008-01-01
if you are just trying to get the pictures off you camara, try to change the settings on you camara to PTP instead of Auto... hope this helps...

Happy New Years!

Bobby

---

### Post by johninbanagher on 2008-01-27
Thanks whos2know for the info as i too have a sony cybershot w55 and was dual booting ubuntu and windoze xp just because i couldnt get my camera to work with ubuntu. i turned it on changed the settings plugged it in and away it went

---

### Post by whos2know on 2008-02-08
johninbanagher,

no problem!!

---

