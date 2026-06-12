---
title: "compiling Xine / XFree86-devel package"
date: 2005-10-19
forum: General Help
---

### Post by nobby_trussin on 2005-10-19
Hi, i'm compiling xine video player and getting the error:

****************************************************************
WARNING! No X11 output plugins will be built.

For some reason, the requirements for building the X11 video
output plugins are not met. That means, that you will NOT be
able to use the resulting xine-lib to watch videos in a window
on any X11-based display (e.g. your desktop).

If this is not what you want, provide the necessary X11 build
dependencies (usually done by installing a package called
XFree86-devel or similar) and run configure again.
****************************************************************

however, ubuntu doesn't seem to have the XFree86-devel package. does anyone know what that is now called or whatever?

thanks

---

### Post by burok on 2005-10-19
i just compilled mplayer and need that

apt-get install x-window-system-dev 

work great :)

---

### Post by mawaru on 2006-10-22
does anyone know what's the best way to install x-windows-system-dev?  I'm finding that there are many packages it depends on...

Thanks for your help!

---

