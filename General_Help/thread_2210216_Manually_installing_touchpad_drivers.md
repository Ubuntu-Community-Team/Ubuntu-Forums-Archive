---
title: "Manually installing touchpad drivers"
date: 2014-03-09
forum: General Help
---

### Post by Harrison_Gentry on 2014-03-09
Hello,

I'm working on a fork of the xf86-input-mtrack driver because it hasn't been updated in three years and is SO close to providing the functionality I want, but not quite there. The project came with an automatic installation script, but the location /usr/local/lib/xorg/modules/input is apparently not the right one because my changed driver is not found by xorg. Where do I need to put my .so and .la files? My Google skills have been no help.

EDIT: SOLVED IT! Woo! For those in the future who need to find these drivers, they're located in /usr/lib/xorg/modules/input.

---

