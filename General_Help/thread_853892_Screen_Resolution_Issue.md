---
title: "Screen Resolution Issue"
date: 2008-07-09
forum: General Help
---

### Post by Sigmaomega on 2008-07-09
After fiddling with my screen resolution on this newly installed Ubuntu (8.04) I found that when a window or drop down box (Applications) docks or touches the left side of the monitor the colors darken across the screen.  Its really annoying, especially when im running a nVidia 8600GT and expect great performance.  Any idea on what it is or how to fix it?

---

### Post by sayakb on 2008-07-09
At a terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Sigmaomega on 2008-07-09
Thanks very much, it worked! huzzah!

---

### Post by Sigmaomega on 2008-07-10
actually it reverted itself now...and keeps reverting itself..is it b/c of the backup files?

---

### Post by Sigmaomega on 2008-07-10
I'm actually thinking that the computer is trying to show objects outside the monitor's left side of the screen.  I tried to drop the resolution down (its currently set on 1440x900 on a 19"WS Hanns G) but it doesnt allow me to.

---

