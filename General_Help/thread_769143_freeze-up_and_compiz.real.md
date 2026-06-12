---
title: "freeze-up and compiz.real"
date: 2008-04-26
forum: General Help
---

### Post by shochatd on 2008-04-26
I was disappointed to discover that this problem continues in 8.04. Sometimes, with compiz effects enabled, I will leave the computer idle for a while and then discover that the display is frozen with a static image from one of the screen savers on the screen. The mouse pointer moves, but I can't seem to unfreeze the display and regain control of the computer. One day I discovered that when this happens, I can still ssh in from another computer. If I then run top, I see a compiz.real process with %MEM > 90, while all other processes have %MEM < 1.0. If I then kill that process, the system comes back to life, with a non-compiz window manager taking over automatically. Is there anything I can do about this (other than to forget about running desktop effects)? My video is Nvidia GeForce 6200 TC, 1680x1050, in case that is relevant. 
Thanks
-- David

---

### Post by Archimedes0212 on 2008-07-24
ctl+alt+bkspace??

That can be quite irritating after some time though

---

