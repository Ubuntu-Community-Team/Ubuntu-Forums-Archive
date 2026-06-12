---
title: "[SOLVED] re-create xorg.conf"
date: 2008-01-17
forum: General Help
---

### Post by charliehubuntu on 2008-01-17
nvidia-settings trashed my xorg.conf. In the process it was supposed to write a backup, which it didn't.

How can I get Ubuntu to re-create xorg.conf the way it created it during install?

---

### Post by alan34 on 2008-01-18
In a terminal. (ctl-alt-F2) or boot in recovery mode.

sudo dpkg-reconfigure -phigh xserver-xorg

then pick the vesa driver, then 

sudo shutdown -r now

Should give you back your GUI.

Good luck

---

