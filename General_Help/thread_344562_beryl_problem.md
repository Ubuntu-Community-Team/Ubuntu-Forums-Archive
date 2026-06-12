---
title: "beryl problem"
date: 2007-01-23
forum: General Help
---

### Post by usien on 2007-01-23
i have previously installed beryl on my laptop by simply installing the packages through synaptic and it worked fine.i had to reinstall ubuntu.after reinstalltion i decided to try compiz and it woked fine too but i wanted to get beryl back so i removed compiz and downloaded synaptic but now it complains about something.i have tried clearing the cache(apt-get clean) and downloaded again but it doesnt work.the beryl-manager runs but it doesnt load the window manager automatically and when i do this manually it gives errors.i installed xserver-xgl before downloading beryl.here is the error:

usien@usien-laptop:~$ beryl-manager
usien@usien-laptop:~$ libGL warning: 3D driver claims to not support visual 0x5b
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present

** (beryl-manager:7148): WARNING **: Beryl caught deadly signal 11
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

### Post by usien on 2007-01-23
anyone?

---

