---
title: "X settings dont stick"
date: 2004-12-09
forum: General Help
---

### Post by vondur on 2004-12-09
I have ubuntu working just fine, and I have installed the Nvidia drivers for my GeForce FX 5200 just fine. (3d works). However the system after logging in or rebooting wants to set the screen resolution to 1600x1200 at 60 hz. I currently using an Apple 17" studio display monitor that I set to use at 1152x864 at 85hz using the system configuration tool. Yet like mentioned eariler it always resets itself back to 1600x1200 at 60 hz.


Thanks

---

### Post by vondur on 2004-12-09
Figured it out myself. I just edited the /etc/X11/XF86 file. I simply changed the first entry under the different color depths to 1152x864 from 1600x1200. Neato.

---

