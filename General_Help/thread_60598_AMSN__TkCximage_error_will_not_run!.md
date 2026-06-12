---
title: "AMSN  TkCximage error: will not run!"
date: 2005-08-28
forum: General Help
---

### Post by cowlip on 2005-08-28
HI, I try to install amsn cvs, but I only get this error.  Configure seems fine, make fails.

> ubuntu ~/Desktop/msn $ make
utils/TkCximage/src/Rules.mk:10: warning: overriding commands for target `utils/TkCximage/src/TkCximage.so'
utils/TkCximage/src/Rules.mk:10: warning: ignoring old commands for target `utils/TkCximage/src/TkCximage.so'
  CXX     utils/TkCximage/src/TkCximage.o
In file included from utils/TkCximage/src/TkCximage.cpp:11:
utils/TkCximage/src/TkCximage.h:23:25: tkPlatDecls.h: No such file or directory
utils/TkCximage/src/TkCximage.cpp: In function `int Tkcximage_Init(Tcl_Interp*)
   ':
utils/TkCximage/src/TkCximage.cpp:159: error: `Tk_InitStubs' undeclared (first
   use this function)
utils/TkCximage/src/TkCximage.cpp:159: error: (Each undeclared identifier is
   reported only once for each function it appears in.)
make: *** [utils/TkCximage/src/TkCximage.o] Error 1


---

