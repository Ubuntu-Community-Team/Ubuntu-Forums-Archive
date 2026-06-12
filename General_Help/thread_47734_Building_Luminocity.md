---
title: "Building Luminocity"
date: 2005-07-09
forum: General Help
---

### Post by chack on 2005-07-09
Hi

I have tried to build Luminocity, but at the module nº 24 this error appear:

: undefined reference to `XF86VidModeQueryVersion'
/usr/X11R6/lib/libGL.a(glxcmds.o)(.text+0x2f1a): In the function `glXGetMscRateOML':
: undefined reference to `XF86VidModeGetModeLine'
collect2: ld devolvió el estado de salida 1 (return exit status 1)
make[3]: *** [luminocity] Error 1
make[3]: Leaving directory `/home/chack/luminocity/src/luminocity/luminocity/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/chack/luminocity/src/luminocity/luminocity/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/chack/luminocity/src/luminocity/luminocity'
make: *** [all] Error 2
*** error during stage build of luminocity: could not build module *** [24/24]

What should I do?

Thanks, 
Rodrigo Aliste P.

---

### Post by subzero on 2005-07-11
Hi

Just wanted to tell, that I'm experincing the same problem on x86 Ubuntu Hoary.

---

