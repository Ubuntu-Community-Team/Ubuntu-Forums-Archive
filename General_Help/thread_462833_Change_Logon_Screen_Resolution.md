---
title: "Change Logon Screen Resolution?"
date: 2007-06-03
forum: General Help
---

### Post by marshall.robert on 2007-06-03
Hi, could someone let me know how to change the resolution of the logon screen? i changed monitors and this one cant handle the stupidly high res its stuck on :P.

cheers
-rob

---

### Post by kellemes on 2007-06-03
You mean GDM right?
I remember it has to do with how the resolution setting in xorg.conf is defined. Can you please post it?

---

### Post by notquitemichael on 2007-06-03
a quick fix is to use dpkg -phgh xserver -reconfigure
that'll allow you to choose your drivers and resolutions default to xorg, but i wouldn't try it if you've never got your hands dirty with xorg.conf

---

