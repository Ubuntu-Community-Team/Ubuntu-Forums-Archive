---
title: "Booting Issue"
date: 2013-01-05
forum: General Help
---

### Post by Tractornuts on 2013-01-05
When I reboot 12.04 I get a booting message, " Out of Frequency" and then it just sets there does 12.12 fix this or is there a work around?

---

### Post by Rocklobster690 on 2013-01-05
Paste the contents of xorg.conf into the thread before doing the following..

After boot, hold down the left shift key and select recovery mode. Open Terminal and backup xorg.conf:

$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

Generate new xorg.conf - [http://ubuntuforums.org/showthread.php?t=1553582](http://ubuntuforums.org/showthread.php?t=1553582)

$ sudo reboot

Let us know the outcome.

---

### Post by tgalati4 on 2013-01-05
Try turning off kernel modeset.  There are several posts around on how to do it.

---

