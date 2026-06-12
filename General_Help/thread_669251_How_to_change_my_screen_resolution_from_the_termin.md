---
title: "How to change my screen resolution from the terminal"
date: 2008-01-16
forum: General Help
---

### Post by coc_21 on 2008-01-16
I changed my screen resolution to 1440 x 900 and now only half of my montior is being used. The display is very small and I cant see anything to change it back to a lower resolution.

---

### Post by geirha on 2008-01-16
You can use xrandr. If you can mange to get a terminal in the visual part of the screen, run ```
xrandr
``` which will list available modes, then ```
xrandr -s 1024x768
``` or whatever mode you want, should change the resolution. 

If you are unable to do this from the running X, you can try using the console. Hit Ctrl+Alt+F1, log in and type the same commands as above, but with DISPLAY=:0 in front:
```
DISPLAY=:0 xrandr
DISPLAY=:0 xrandr -s 1024x768
```
xrandr might appear to hang when run from the console, but it just needs to have the X shown on screen, so after typing a xrandr command like that, Switch to X with Ctrl+Alt+F7, then back again with Ctrl+Alt+F1.

---

### Post by coc_21 on 2008-01-16
run gdm to resolve this issue

---

