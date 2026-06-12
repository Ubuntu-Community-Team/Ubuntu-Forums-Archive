---
title: "blender doesnt start anymore"
date: 2008-05-02
forum: General Help
---

### Post by meteozguz on 2008-05-02
Hi my current ubuntu is 8.04 hardy kernel linux 2.6.24-16-generic gnome 2.22.1

I am using blender since two weeks but today it just stoped to start
I removed it and reinstalled again but didnt work

---

### Post by meteozguz on 2008-05-03
I solved my problem


asdf@ubuntu:~$ blender
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.5.2.
Checking for installed Python... got it!
Xlib:  extension "GLX" missing on display ":0.0".
intern/ghost/intern/GHOST_WindowX11.cpp:105: X11 glxChooseVisual() failed for OpenGL, verify working openGL system!
ERROR: Unable to open Blender window
asdf@ubuntu:~$ 


I opened hardware drivers and enabled my NVIDIA driver but the interesting thing is I was already enabled that driver

Later I wanted to test the solution and I removed the driver than I restarted and I was able to start blender

---

