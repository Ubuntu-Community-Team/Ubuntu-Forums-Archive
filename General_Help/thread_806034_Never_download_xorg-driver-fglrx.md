---
title: "Never download xorg-driver-fglrx?"
date: 2008-05-24
forum: General Help
---

### Post by UltraSonicSite on 2008-05-24
A few seconds ago games worked.

I tried to run Phun.

Got an error:
```
ultrasonicsite@ubuntu:~/Desktop/Phun$ ./phun
workdir = /home/ultrasonicsite/Desktop/Phun/
Loading language English...
Parsing /home/ultrasonicsite/Desktop/Phun/autoexec.cfg...
Creating window...
!! ERROR: Exception caught in main: Couldn't set video mode, SDL-error: Couldn't find matching GLX visual
Exception caught: Couldn't set video mode, SDL-error: Couldn't find matching GLX visual
!! ERROR: Exception caught: Couldn't set video mode, SDL-error: Couldn't find matching GLX visual

```



Tried installing a random file, randomly installed xorg-driver-fglrx.

Now I get

```

     =======================|  DirectFB 1.0.1  |=======================
          (c) 2001-2007  The DirectFB Organization (directfb.org)
          (c) 2000-2004  Convergence (integrated media) GmbH
        ------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2008-04-08 15:15) 
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
!! ERROR: Exception caught in main: Couldn't init SDL: DirectFBCreate: Initialization error!
Exception caught: Couldn't init SDL: DirectFBCreate: Initialization error!
!! ERROR: Exception caught: Couldn't init SDL: DirectFBCreate: Initialization error!


```



And I know that when the games stop working, linux stops working, so I'm not going to reboot because once I'm stuck in the console it's game over =P

Any help with this er, tiny problem? x)

---

### Post by UltraSonicSite on 2008-05-24
Nooooo! Frozen-Bubble stopped working!

---

### Post by UltraSonicSite on 2008-05-24
Nevermind, I'll check out another linux dist. I hear Vector is good for old computers.

---

