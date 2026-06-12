---
title: "Disabling Hardware Cursor"
date: 2018-09-04
forum: General Help
---

### Post by antisthenes2 on 2018-09-04
In Ubuntu 14.04 LTS using the X.Org X server display driver, redshift (the colour temperature adjustment tool) doesn't affect the colour of my mouse cursor. The issue seems to be that  the graphics driver is configured to use hardware cursors. According to  the redshift website, some graphics drivers have an option to disable  hardware cursors in xorg.conf, though this file doesn't exist anymore in Ubuntu.

How then can I disable the hardware cursor?

---

### Post by QIII on 2018-09-04
Hello!

It would be helpful if you could provide some information about the GPU and driver being used.

---

### Post by Holger_Gehrke on 2018-09-04
Read the manual page for xorg.conf ('man 5 xorg.conf' in a terminal). You can have an xorg.conf. The options specified in that file will be used in preference of the automatically configured settings. You only need to write the section(s) and option(s) you need, everything else will be configured automatically.

Holger

---

### Post by antisthenes2 on 2018-09-05
Hello!

The GPU is an NVIDIA GeForce 9400M and the driver is the open source X.Org X server nouveau (the other (proprietary) drivers that are available for this GPU do not work well; only the open source one does).

I've read elsewhere that creating the xorg.conf file is not recommended. Is there another (simpler) way of disabling the hardware cursor?

---

### Post by antisthenes2 on 2018-09-16
Bump.

---

### Post by antisthenes2 on 2018-09-17
So, I created an xorg.conf file and placed it in /etc/X11. In the file, I added only this line: Option "HWCursor" "off", which, from what I've read, is what disables the hardware cursor. I restarted the computer, and now Ubuntu does not load (during the boot, the screen tears and stays like that).

I can access the hard disk by booting from a LiveUSB, but I'm unable to delete the problematic file because I do not have the necessary permissions. How can I get the necessary permissions, and how can I disable the hardware cursor correctly?

---

### Post by ajgreeny on 2018-09-18
**Please do not create duplicate or near duplicfate posts about the same subject;** it is confusing for all including you and dilutes the forum's ability to help.

See [https://ubuntuforums.org/showthread.php?t=2401413&p=13801707#post13801707](https://ubuntuforums.org/showthread.php?t=2401413&p=13801707#post13801707)

Closed

---

