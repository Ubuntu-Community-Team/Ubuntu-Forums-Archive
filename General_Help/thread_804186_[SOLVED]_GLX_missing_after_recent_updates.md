---
title: "[SOLVED] GLX missing after recent updates"
date: 2008-05-22
forum: General Help
---

### Post by Azraelthe7th on 2008-05-22
Compiz (as well as any OpenGL applications) was working well until today's update.  For some reason, when I logged out and went back in, I would get the "XGL not present" error.  Using the "glxconfig" command, it gives me the "GLX is missing on display" ":0.0".

I've already tried making a symbolic link to "libglx.so", and that has failed.

I'm using the 173.08 beta drivers to get the GeForce 9600 GT working, so the Ubuntu restricted modules, as well as EnvyNG aren't useable options.  Any suggestions?

---

### Post by Azraelthe7th on 2008-05-22
Never mind, I was able to fix it by re-installing the beta drivers without changing the X server settings.

---

