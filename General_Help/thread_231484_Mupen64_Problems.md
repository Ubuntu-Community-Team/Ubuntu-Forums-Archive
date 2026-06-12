---
title: "Mupen64 Problems"
date: 2006-08-07
forum: General Help
---

### Post by Darth Muzzy on 2006-08-07
I've been having some issue with Mupen64.
The only video plugin that works is the Mupen64 software gfx plugin, which is extreamly slow.

When I try and use the Glide64 plugin, I get this problem when I try and load a game:

[blight's SDL input plugin]: Couldn't open blight_input.conf for reading: No such file or directory
[blight's SDL input plugin]: version 0.0.10 initialized.
(II) Initializing SDL video subsystem...
(II) Getting video info...
(II) Setting video mode 1024x768...
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
(EE) Error setting videomode 1024x768: Couldn't find matching GLX visual

(mupen64:14421): GLib-WARNING **: g_main_context_prepare(): main loop already active in another thread

(mupen64:14421): GLib-WARNING **: g_main_context_check() called recursively from within a source's check() or prepare() member.

GLib-ERROR **: file gmain.c: line 1880 (g_main_dispatch): assertion failed: (source)
aborting...
Aborted


I've tried a using different window resolutions (I had problems with that when I was first setting up Zsnes on my comp)

---

### Post by PatrickMay16 on 2006-08-07
Hello there. 
From that output, it seems like you may not have hardware accelerated 3D, which the other graphics plugins need.
What video card do you have?

Also, could you give me the output of this command:
```

glxinfo | grep render

```

- Patrick

---

### Post by Darth Muzzy on 2006-08-07
I have a GeForce6600 delux.

output:

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by PatrickMay16 on 2006-08-07
It looks like you need to install Nvidia's display driver. This page has exactly how to do it:
[http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation_through_APT](http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation_through_APT)

Good luck.

---

### Post by rsikes2290 on 2006-10-26
hi, Im using Mac OSX and i have Mupen64, Everytime i start up SuperMario 64 it laggs and laggs and laggs. And i cant stand it. can somebody help me! thanks

---

