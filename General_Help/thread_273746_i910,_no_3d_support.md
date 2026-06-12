---
title: "i910, no 3d support"
date: 2006-10-08
forum: General Help
---

### Post by Brenlae on 2006-10-08
I'm curious, i have an onboard i910GL (I had a 6600GT, but it just died on me) and I want 3D to start working - is there anything I can do, or am I doomed to have no 3D?

Also, with my 6600GT, totem-xine had fine colours, but now using my i910, the colours are way too bright (too much contrast/saturation).

Anyway, any help would be much appreciated. :)

---

### Post by Brenlae on 2006-10-08
Ok, I figured out how to fix the video problem, but still no 3d.

Here's my glxinfo output:

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

---

### Post by Brenlae on 2006-10-09
*bump*

Does anyone have any idea how I could get 3D working for my i910?

---

### Post by StevenYap on 2006-10-09
Looks like you're missing the glx extension.  Does the Module section of your /etc/X11/xorg.conf contains a line like:   Load "glx" ?

Here's how mine looks:

```
Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection
```

---

