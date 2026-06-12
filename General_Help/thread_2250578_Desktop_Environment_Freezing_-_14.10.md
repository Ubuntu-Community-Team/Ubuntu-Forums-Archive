---
title: "Desktop Environment Freezing - 14.10"
date: 2014-10-29
forum: General Help
---

### Post by iason on 2014-10-29
Hi,

Looking to get some direction for identifying the cause of my desktop to freeze.  Everything worked well up until i updated to 14.10, I couldn't figure out what the issue was, after a few rebuilds I noticed it happened when launching gnome-do.  I could drop into another tty and do a top, but nothing stood out, tried looking through all logs and couldn't identify anything that stood out.   basically running a clean build on an hp elitebook 840, mainly just vmware player and cinnamon installed.  Thought  had it salved but everything just frooze after loading a new usb thumb drive and the DE just locked up.  What is the best way to identity the cause?  anything in logs in particular I may be over looking?  


grep EE /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.464] (II) XINPUT: Adding extended input device "Atmel Atmel maXTouch Digitizer" (type: TOUCHSCREEN, id 9)
[    17.508] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm

---

