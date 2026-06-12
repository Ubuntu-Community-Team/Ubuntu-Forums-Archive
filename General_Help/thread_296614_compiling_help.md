---
title: "compiling help"
date: 2006-11-09
forum: General Help
---

### Post by kkellner on 2006-11-09
hello-
I am trying to compile beryl 0.1.2 for practice.  I'm a little inexperienced at compiling, and I've managed to fix a few errors so far, but not this one, while compiling beryl-core-0.1.2 (sudo make install):

```
-lm
../mesa/lib/libGL.a(glxext.o): In function `__glXErrorString':glxext.c:(.text+0x4ca): undefined reference to `__stack_chk_fail_local'
../mesa/lib/libGL.a(glxextensions.o): In function `__glXCalculateUsableGLExtensions':glxextensions.c:(.text+0x6b8): undefined reference to `__stack_chk_fail_local'
../mesa/lib/libGL.a(glxextensions.o): In function `__glXCalculateUsableExtensions':glxextensions.c:(.text+0x804): undefined reference to `__stack_chk_fail_local'
../mesa/lib/libGL.a(glapi.o): In function `_glapi_add_dispatch':glapi.c:(.text+0x10891): undefined reference to `__stack_chk_fail_local'
collect2: ld returned 1 exit status
make[1]: *** [beryl-xgl] Error 1
make[1]: Leaving directory `/home/ken/Desktop/beryl/beryl-core-0.1.2/src'
make: *** [install-recursive] Error 1
```

Anyone have any ideas about this?  Am I missing a package?  Everything seemed to be going normally until this point.

Thanks in advance.

---

### Post by bukwirm on 2006-11-09
Make sure you have all the OpenGL (Mesa) library packages and the development version of those packages (usually called *package_name*-dev).

---

### Post by kkellner on 2006-11-09
thanks for your response.  I think I have all the mesa packages installed - I double checked in synaptic and found that I had libgl1-mesa, libgl1-mesa-dev, libgl-mesa-dri, libglu1-mesa, libglu1-mesa-dev, mesa-common-dev, and mesa-utils installed.  There are other packages called mesa-swrast, etc. and libosmesa6, etc.  but when I try to install those synaptic wants to remove x-window-system-core and I don't think I want to do that.  Any ideas?

---

