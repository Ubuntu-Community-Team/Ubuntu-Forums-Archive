---
title: "Restore standard graphic drivers"
date: 2012-11-27
forum: General Help
---

### Post by Ofless on 2012-11-27
Hey folks,

I'm experiencing the following problem:
Out of curiosity I started messing around with my graphic drivers and I messed them up so that I can't run unity anymore. Instead, the system keeps falling back into unity-2d-mode.

This was a mistake. I can't even tell what I exactly did but now even in unity-2d the font rendering is really bad, so that even the text on the main panel looks yellowish.

I'm running Ubuntu 12.04 on a thinkpad T400 with a Intel GMA4500 integrated graphics card and now I would like to restore the standard out-of-the-box drivers/settings but I can't find any information on the web how to do it.

Can anyone maybe help me?

Here are the outputs of glxinfo if that might be helpful:
direct rendering: Yes
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset 
OpenGL version string: 2.1 Mesa 9.1-devel (git-5dbc84e precise-oibaf-ppa)
OpenGL shading language version string: 1.20
OpenGL extensions:

Thank you in advance!

EDIT:
Every time I run apt-get autoremove or update or something the following errors show up:
...
Trigger für libc-bin werden verarbeitet ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/lib/i386-linux-gnu/libEGL.so.1 ist kein symbolischer Link
/sbin/ldconfig.real: /usr/lib/i386-linux-gnu/libGL.so.1 ist kein symbolischer Link
/sbin/ldconfig.real: /usr/lib/i386-linux-gnu/libGLw.so.1 ist kein symbolischer Link
/sbin/ldconfig.real: /usr/lib/x86_64-linux-gnu/libEGL.so.1 ist kein symbolischer Link
/sbin/ldconfig.real: /usr/lib/x86_64-linux-gnu/libGL.so.1 ist kein symbolischer Link
/sbin/ldconfig.real: /usr/lib/x86_64-linux-gnu/libGLw.so.1 ist kein symbolischer Link

---

### Post by Cheesemill on 2012-11-27
I'm not sure exactly what you've done but it would help if you told us step by step.

There is only one driver available for Intel graphics, and it was installed along with Ubuntu, it's not possible to use another driver as there aren't any.

---

