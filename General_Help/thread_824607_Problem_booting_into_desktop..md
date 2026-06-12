---
title: "Problem booting into desktop."
date: 2008-06-10
forum: General Help
---

### Post by D46 on 2008-06-10
Booting off of both live CD and after installed to hard disk.

X seems to hang before I'm able to log in. Keyboard seems unresponsive, although I'm still able to use it to RSEIUB. Cursor displays an X and I'm still able to move it.

Found quite a few hundred lines of this within /var/log/gdm/:0.log
```
Tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.
```

/var/log/Xorg.0.log seems normal(As far as I can tell), ending with..
```
(--) NV(0): Trying to load detection on VGA0"
```

xorg.conf is default.
Videocard is Nvidia Corporation GeForce 8400 GS

Running 8.04

---

### Post by D46 on 2008-06-10
No reply. :\

Driver problems?
Downgrade Xorg?

---

