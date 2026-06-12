---
title: "PyPanel install error"
date: 2005-08-12
forum: General Help
---

### Post by plewisfdx on 2005-08-12
Here is the error I get when I try to install PyPanel:

```
phil@laptop:~/d/temp/PyPanel-2.2$ python setup.py install
running install
running build
running build_ext
building 'ppmodule' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O3 -Wall -Wstrict-prototypes -fPIC -DHAVE_XFT=1 -I/usr/X11R6/include -I/usr/include/freetype2 -I/usr/include/python2.4 -c ppmodule.c -o build/temp.linux-i686-2.4/ppmodule.o -Wall
ppmodule.c:34:25: X11/Xft/Xft.h: No such file or directory
ppmodule.c:37: error: syntax error before '*' token
ppmodule.c:37: warning: type defaults to `int' in declaration of `draw'
ppmodule.c:37: warning: data definition has no type or storage class
ppmodule.c:38: error: syntax error before '*' token
ppmodule.c:38: warning: type defaults to `int' in declaration of `xf'
ppmodule.c:38: warning: data definition has no type or storage class
ppmodule.c: In function `_ppfont':
ppmodule.c:68: error: `XftColor' undeclared (first use in this function)
ppmodule.c:68: error: (Each undeclared identifier is reported only once
ppmodule.c:68: error: for each function it appears in.)
ppmodule.c:68: error: syntax error before "xftcol"
ppmodule.c:69: error: `XGlyphInfo' undeclared (first use in this function)
ppmodule.c:70: error: `XRenderColor' undeclared (first use in this function)
ppmodule.c:88: warning: implicit declaration of function `XftTextExtentsUtf8'
ppmodule.c:88: error: `ginfo' undeclared (first use in this function)
ppmodule.c:97: error: request for member `ascent' in something not a structure or union
ppmodule.c:97: error: request for member `ascent' in something not a structure or union
ppmodule.c:97: error: request for member `descent' in something not a structure or union
ppmodule.c:98: error: `rcol' undeclared (first use in this function)
ppmodule.c:102: warning: implicit declaration of function `XftColorAllocValue'
ppmodule.c:102: error: `xftcol' undeclared (first use in this function)
ppmodule.c:103: warning: implicit declaration of function `XftDrawStringUtf8'
ppmodule.c:104: warning: implicit declaration of function `XftColorFree'
ppmodule.c: In function `_ppfontsize':
ppmodule.c:123: error: `XGlyphInfo' undeclared (first use in this function)
ppmodule.c:123: error: syntax error before "ginfo"
ppmodule.c:133: error: `ginfo' undeclared (first use in this function)
ppmodule.c: In function `_ppinit':
ppmodule.c:256: warning: implicit declaration of function `XftFontOpenXlfd'
ppmodule.c:256: warning: assignment makes pointer from integer without a cast
ppmodule.c:258: warning: implicit declaration of function `XftFontOpenName'
ppmodule.c:258: warning: assignment makes pointer from integer without a cast
ppmodule.c:262: warning: implicit declaration of function `XftDrawCreate'
ppmodule.c:262: warning: assignment makes pointer from integer without a cast
error: command 'gcc' failed with exit status 1

```


I run HH / Openbox (only, no Gnome), on a Dell Inspiron 2500 Laptop.

I installed the packages that it complained about when I tried installing pypanel the first time.

1. python-dev
2. Imlib2
3. python-xlib

thanks for the help.

phil

---

