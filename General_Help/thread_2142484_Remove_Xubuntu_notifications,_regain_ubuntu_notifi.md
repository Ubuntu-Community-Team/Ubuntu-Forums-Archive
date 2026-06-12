---
title: "Remove Xubuntu notifications, regain ubuntu notifications"
date: 2013-05-05
forum: General Help
---

### Post by dh04000 on 2013-05-05
I installed xubuntu-desktop package ad it change the style of my desktop volume notification bubble form the corner to a square in the center of the screen.

I removed xubuntu-desktop package and logged out then in, but no change...

How do I fix this?

---

### Post by romain.astie on 2013-05-05
Try running```
sudo apt-get purge xubuntu-desktop
``` to get rid of anything left on your system that pertains to that package.

---

### Post by dh04000 on 2013-05-05
Thanks, that did the trick.

---

