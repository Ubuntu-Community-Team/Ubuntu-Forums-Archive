---
title: "Screen resolution for projector"
date: 2006-07-15
forum: General Help
---

### Post by anandrd on 2006-07-15
I am sorry if I am asking an infinitely repeated question, but how do I change my screen resolution? I am currently running at the optimal (1680x1050) but I need to run at 1280x800 or lower when I use the laptop with a projector. (Otherwise the projected image is fuzzy and cropped).

My xrandr output looks like this

```

 SZ:    Pixels          Physical       Refresh
*0   1680 x 1050   ( 331mm x 212mm )  *60
 1   1280 x 1024   ( 331mm x 212mm )   60
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none

```

However trying to do "xrandr -s 1" crashes X. I tried different solutions like adding modeline to the xorg.conf but none worked. For reference I am attaching my Xorg.conf (named myxorg.txt). I have Intel integrated graphics (i915)

Thanks in advance.

---

### Post by reacocard on 2006-07-15
System -> Preferences -> Screen Resolution

---

### Post by anandrd on 2006-07-15
I am using KDE so the counter-part will be "System Settings > Display > Resolution." That's the first thing I tried. I see 1680x1050 and 1280x800 there (the current being 1680x1050). However, setting it to 1280x800 crashes X.

---

