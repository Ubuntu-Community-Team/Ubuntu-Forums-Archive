---
title: "can't run 3ddesk on ubuntu6.1"
date: 2007-02-24
forum: General Help
---

### Post by helai on 2007-02-24
when i try to run 3ddesk on ubuntu 6.1 ,but get the error messages as below
how to avoide this?
thanks in advance

lenovo@lenovo-desktop:~$ 3ddesk
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

---

### Post by bigken on 2007-02-24
I dont think you have the right drivers installed for your video card 
what make is it ?

---

### Post by dcstar on 2007-02-24
> **helai said:**
> when i try to run 3ddesk on ubuntu 6.1 ,but get the error messages as below
how to avoide this?
thanks in advance

lenovo@lenovo-desktop:~$ 3ddesk
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

Do this in a terminal:
```
glxinfo
``` and look for the "Direct Rendering" line - it should say yes if you have 3D working on your video card.

---

