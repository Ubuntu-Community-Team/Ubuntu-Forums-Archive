---
title: "No graphics even in Edgy Install CD"
date: 2006-10-31
forum: General Help
---

### Post by Roobert on 2006-10-31
My graphics have been broken ever since the Dapper-->Edgy upgrade. I'm trying to reinstall from the Live CD, but the graphics remain broken, even when booting from the CD! I get as far as the main menu, where I select 'Start or Install Ubuntu'. Thereafter, everything is black. 

I'm using the ATI X300 driver.

Any ideas?

---

### Post by jimbonnet on 2006-10-31
Try switching to vesa driver in /etc/X11/xorg.conf I have the same card and had the same problem. Also choose something like 1024x768 resolution to get you going.. then grab the fglrx stuff from apt or ati sources. my x300 card in dell 9150 is working just fine now.

jim

---

### Post by Roobert on 2006-10-31
No go. I've tried every driver: vesa, vga, radeon, ati, fglrx, all with no display.

---

