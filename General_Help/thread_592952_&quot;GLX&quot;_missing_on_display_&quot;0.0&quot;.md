---
title: "&quot;GLX&quot; missing on display &quot;:0.0&quot;? trying to run blender"
date: 2007-10-26
forum: General Help
---

### Post by Bubs on 2007-10-26
I get this when I try to run blender from terminal.  I installed nvidia-glx-new from sysnaptic and restarted x before I did this.
```

bubs@bubs-desktop:~$ blender
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.4.4.
Checking for installed Python... got it!
Xlib:  extension "GLX" missing on display ":0.0".
intern/ghost/intern/GHOST_WindowX11.cpp:103: X11 glxChooseVisual() failed for OpenGL, verify working openGL system!
ERROR: Unable to open Blender window
bubs@bubs-desktop:~$ 
```

---

### Post by Bubs on 2007-10-26
I used envy to install the drivers.  instead of synaptic...

but this may sound stupid but...  I got to thinking that a full system restart would have been called for instead of restarting X...  I never thought of that and never tried that.  but now it works I don't really care.  but try it yif you have a similar problem...

---

