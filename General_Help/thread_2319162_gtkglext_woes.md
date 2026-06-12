---
title: "gtkglext woes"
date: 2016-04-01
forum: General Help
---

### Post by andy139 on 2016-04-01
Trying to install GSVIT FDTD analysis software.

Running ```
./configure
``` comes up all clear.

```
dag0r@WYVERN:~/Downloads/gsvit-1.8.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.0.0... yes (version 2.46.2)
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... yes (version 2.24.28)
checking for GWYDDION... yes
Gwyddion: default path used.
CUDA: default path used.
NVCC version is nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2015 NVIDIA Corporation
Built on Tue_Aug_11_14:27:32_CDT_2015
Cuda compilation tools, release 7.5, V7.5.17, configuring with CUDA support.
configure: creating ./config.status
config.status: creating Makefile
config.status: creating gsvit.spec
config.status: creating src2d/Makefile
config.status: creating src3d/Makefile
config.status: creating tests/Makefile
config.status: creating tests/test01/Makefile
config.status: creating tests/test02/Makefile
config.status: creating tests/test03/Makefile
config.status: creating tests/test04/Makefile
config.status: creating tests/test05/Makefile
config.status: creating tests/test06/Makefile
config.status: creating tests/selftests/Makefile
config.status: creating data/Makefile
config.status: creating data/spectra/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
```


Running ```
make
``` I hit an error I am unsure how to rectify

I get the following message:

```
In file included from /usr/include/gtkglext-1.0/gtk/gtkgl.h:22:0,
                 from xsvit.c:27:
/usr/include/gtkglext-1.0/gdk/gdkgl.h:22:29: fatal error: gdkglext-config.h: No such file or directory
 #include <gdkglext-config.h>
                             ^
compilation terminated.
Makefile:942: recipe for target 'xsvit-xsvit.o' failed
make[2]: *** [xsvit-xsvit.o] Error 1
make[2]: Leaving directory '/home/dag0r/Downloads/gsvit-1.8.1/src3d'
Makefile:273: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/dag0r/Downloads/gsvit-1.8.1'
Makefile:209: recipe for target 'all' failed
make: *** [all] Error 2
```

I opened the file gdkgl.h and it shows the following (after licensing comments)
```


#ifndef __GDK_GL_H__
#define __GDK_GL_H__

#include <gdkglext-config.h>

#include <gdk/gdkgldefs.h>
#include <gdk/gdkglversion.h>
#include <gdk/gdkgltokens.h>
#include <gdk/gdkgltypes.h>
#include <gdk/gdkglenumtypes.h>
#include <gdk/gdkglinit.h>
#include <gdk/gdkglquery.h>
```

I have managed to track down the file ```
gdkglext-config.h
``` in ```
/usr/lib/gtkglext-1.0/include/
```

Do the #include commands need modifying here? This is a bit beyond my level of knowledge!

Thanks in advance

---

### Post by steeldriver on 2016-04-01
How did you install libgtkglext? What does 

```

pkg-config --cflags gdkglext-x11-1.0

```
say?

---

### Post by andy139 on 2016-04-02
Thanks for getting back

Output of pkg-config --cflags gdkglext-x11-1.0
```

dag0r@WYVERN:~$ pkg-config --cflags gdkglext-x11-1.0
-pthread -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng12 -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/gtkglext-1.0 -I/usr/lib/gtkglext-1.0/include 
```

Installed using ```
dag0r@WYVERN:~$ sudo apt-get install libgtkglext1

```

I also have libgtk 2.0 and 3.0 and dev versions installed using apt-get

---

### Post by steeldriver on 2016-04-02
I can't reproduce this error on my Ubuntu 14.04 box - but unfortunately I can't try it with CUDA 7.5 because it breaks the display driver

Since pkg-config appears to detect the relevant include path (i.e. -I/usr/lib/gtkglext-1.0/include), I can only guess it's something about CUDA that is causing it to ignore the Makefile variable (which seems to be GWYDDION_CFLAGS)

---

