---
title: "steam missing dependencies 21.10"
date: 2021-11-08
forum: General Help
---

### Post by yaminb on 2021-11-08
One of the recent updates broke my steam. It appears to be missing some 32bit libraries
I tried getting a few of them, but it doesn't look like it exists.


Running Steam on ubuntu 21.10 64-bit
STEAM_RUNTIME is disabled by the user
Error: You are missing the following 32-bit libraries, and Steam may not run:
libpipewire-0.3.so.0
libva.so.2
libva-drm.so.2
libva.so.2
libva-x11.so.2
Can't find 'steam-runtime-check-requirements', continuing anyway
WARNING: Using default/fallback debugger launch


E: Unable to locate package libva-x11:i386

---

### Post by Dennis N on 2021-11-08
> **yaminb said:**
> 
E: Unable to locate package libva-x11:i386

The correct package is: **libva-x11-2:i386 **

From Ubuntu package search:
```
/usr/lib/i386-linux-gnu/libva-x11.so.2 	libva-x11-2 [i386] 
```

---

### Post by yaminb on 2021-11-08
thanks. Looks like I got all the dependencies in order, but it still won't launch.

unning Steam on ubuntu 21.10 64-bit
STEAM_RUNTIME is enabled automatically
Steam runtime environment up-to-date!
Steam client's requirements are satisfied
WARNING: Using default/fallback debugger launch

---

### Post by yaminb on 2021-11-09
Not sure what happened, but it seems to have been resolved.

---

