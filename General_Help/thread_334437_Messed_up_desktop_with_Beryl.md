---
title: "Messed up desktop with Beryl"
date: 2007-01-08
forum: General Help
---

### Post by FuturePilot on 2007-01-08
I tried to install Beryl on Edgy and I got everything installed but when I start Beryl it messes up my display. I'm not sure what I did wrong. I have a Nvidia GeForce 2 Go. Help!
[IMG]http://img218.imageshack.us/img218/8566/screenshotyy5.png[/IMG]

---

### Post by FuturePilot on 2007-01-09
Ok, well I fixed that problem by changing the bit depth from 16 to 24 in the xorg.conf file. But  now I've got another little problem. Beryl seems to freeze up my computer a lot. It seems like it'll freeze up for sure if I try to play music or videos but it's also just randomly frozen on me. And there's nothing I can do, it's completely frozen. Could it be that my hardware isn't good enough? This is sort of an old laptop
Intel Pentium 4m
Nvidia GeForce 2 Go (32 MB on-board RAM)
768 MB RAM

---

### Post by Jaygo333 on 2007-01-09
I also seem to have thee same problem.
My windows decorator disapear and Ubuntu starts acting weied, windows are black, terminal opens by itself and such.

---

### Post by Waappu on 2007-01-09
Hi

Try disable water and blur plugins from beryl setting manager

---

### Post by d3v1ant_0n3 on 2007-01-09
> **FuturePilot said:**
> Ok, well I fixed that problem by changing the bit depth from 16 to 24 in the xorg.conf file. But  now I've got another little problem. Beryl seems to freeze up my computer a lot. It seems like it'll freeze up for sure if I try to play music or videos but it's also just randomly frozen on me. And there's nothing I can do, it's completely frozen. Could it be that my hardware isn't good enough? This is sort of an old laptop
Intel Pentium 4m
Nvidia GeForce 2 Go (32 MB on-board RAM)
768 MB RAM

Hardware wise, you're not that different from me (except I have an Intel 845 graphics chipset). I'd definitely recommend disabling water and blurfx. Some of the fancier animations can be quite CPU intensive, as can 3dWorld, Transaprent Cube, etc.

---

### Post by FuturePilot on 2007-01-09
I disabled the water effects and the blur, but it's still freezing up on me. It seems to freeze when I go to close a window or move a window.

---

### Post by FuturePilot on 2007-01-09
I started beryl-manager from a terminal and this is what I got, not sure if it has anything to do with this or not:
```
~$ beryl-manager
~$ XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: No GLXFBConfig for default depth, falling back on visinfo.

** (process:4753): WARNING **: get_setting_is_integrated not found in backend ini

** (process:4753): WARNING **: get_setting_is_read_only not found in backend ini

** (process:4753): WARNING **: get_setting_is_integrated not found in backend ini

** (process:4753): WARNING **: get_setting_is_read_only not found in backend ini
Initiating splash
Reloading all options.


```

---

### Post by FuturePilot on 2007-01-09
I started beryl from a terminal and left it open. It doesn't seem to freeze if I keep the terminal open, but I know the minute I close it it's going to freeze. But here's the errors that appear when it would normally freeze:
```
(emerald:6180): Gdk-CRITICAL **: gdk_drawable_unref: assertion `GDK_IS_DRAWABLE (drawable)' failed
Reloading...

```
These will appear if I start adjusting things in the Emerald Theme Manager.:-k
Does anyone know what's going on here? This is really annoying.

---

### Post by Waappu on 2007-01-09
Hi

Press Alt+F2 and type beryl-manager
So you don't need to have terminal open =)

---

### Post by FuturePilot on 2007-01-09
That's usually what I do and then a few minutes later it freezes. If I leave the terminal open while running it gives me error messages when it would normally freeze.

---

