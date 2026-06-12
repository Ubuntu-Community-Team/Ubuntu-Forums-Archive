---
title: "Confused with gtk+"
date: 2007-09-11
forum: General Help
---

### Post by Imsati on 2007-09-11
I'm trying to install a Front End for an on-line RPG. I have to compile it. I'm following the directions in the Install file, but am getting stuck with the following:

jason@JasonU:/media/Jason_Linux/Simu/warlock-0.5-pre6$ ./configure --without-spidermonkey
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for Win32... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for flex... no
checking for lex... no
checking for bison... no
checking for byacc... no
checking for GC_malloc in -lgc... yes
checking for SpiderMonkey... no
checking for pcre-config... /usr/bin/pcre-config
checking return type of signal handlers... void
checking for memmove... yes
checking for strerror... yes
checking for timegm... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EGG... configure: error: Package requirements (gtk+-2.0 >= 2.5.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EGG_CFLAGS
and EGG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

jason@JasonU:/media/Jason_Linux/Simu/warlock-0.5-pre6$ 

Where should I go from here? I looked for gtk+ on the web, but what I found seemed really odd and I wasn't sure how to compile it or download it.

--Jay

---

### Post by geraldm on 2007-09-11
From source:
[ftp://ftp.gtk.org/pub/gtk/v2.8/gtk+-2.8.20.tar.bz2](ftp://ftp.gtk.org/pub/gtk/v2.8/gtk+-2.8.20.tar.bz2)
Note the dependencies:  you will also need glib, atk, and pango

There should be a recent gtk+-... from ubuntu, as it gets used a lot.  Also get the *-dev package
if you take it from ubuntu.

Gerald

---

### Post by Imsati on 2007-09-11
> **geraldm said:**
> From source:
[ftp://ftp.gtk.org/pub/gtk/v2.8/gtk+-2.8.20.tar.bz2](ftp://ftp.gtk.org/pub/gtk/v2.8/gtk+-2.8.20.tar.bz2)
Note the dependencies:  you will also need glib, atk, and pango

There should be a recent gtk+-... from ubuntu, as it gets used a lot.  Also get the *-dev package
if you take it from ubuntu.

Gerald

Thanks for the link. Where would I find the -dev package? I looked in Synaptic and only found gtk+ themes.

---

### Post by Imsati on 2007-09-12
Hmm, well I got hte GTk+ installed, then went back to try the package I was having trouble to bgein with and got the same error.

>>checking for EGG... configure: error: Package requirements (gtk+-2.0 >= 2.5.0) were not met:

Could the program I'm trying to install maybe need something specifically between those two versions?

---

### Post by geraldm on 2007-09-12
Linux works out of a cache; after installing the program you need to do one of these:
1) as root user: ldconfig
2) reboot
either of those will clear out the obsolete cache.

Gerald

---

### Post by K.Mandla on 2007-09-12
I could be wrong, but I think you want libgtk2.0-dev

[http://packages.ubuntu.com/feisty/libdevel/libgtk2.0-dev](http://packages.ubuntu.com/feisty/libdevel/libgtk2.0-dev)

I'd install it via aptitude, rather than grabbing something from elsewhere on the net, if I were you.

---

### Post by Imsati on 2007-09-12
Thanks for the GTK link. I made a bit more progress and figureed out a few more things, but now I'm getting this...

checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.8 gthread-2.0 libglade-2.0 gconf-2.0) were not met:

No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

libglade and gconf2 are installed as per Synaptic. I'm ready to just say screw it with trying to do this and finding another way

---

### Post by K.Mandla on 2007-09-12
I can't say for sure but if you look for development versions of those packages, that might be what's missing.

Like the libgtk2.0-dev package I linked to, I find that I usually need the *-dev version to compile. 

Check Synaptic or the package search pages for something like libglade-dev and/or gconf2-dev. I'm not sure what they'd be.

---

