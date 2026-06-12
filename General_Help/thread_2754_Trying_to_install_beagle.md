---
title: "Trying to install beagle"
date: 2004-10-31
forum: General Help
---

### Post by mrchocobo on 2004-10-31
i have a problem trying to intall beagle following this howto: [http://wiki.ubuntu.com/BeagleInstallHowto](http://wiki.ubuntu.com/BeagleInstallHowto)


at the end, when i try to build beagle with ./autogen.sh && make. it fails with this message:

checking which mozilla to use... configure: error: no mozilla installation found


mozilla is installed. so i don't know why is it saying this. any ideas?

---

### Post by mrchocobo on 2004-10-31
ok i see that it is because pkgconfig says that this package it's not installed. how can i install it to make pkgconfig able to see it?  :???:

---

### Post by mrchocobo on 2004-10-31
ok, i solved it

---

### Post by shoelessmike on 2004-11-12
Hey Mr. C, could you tell me how you beagle to notice mozilla?
Thanks ...

---

### Post by shoelessmike on 2004-11-12
Figured as long as beagle problems were here ...
I've been working on installing beagle and got to just about the end. 

```
bubba@bubbashack:~/cvs/beagle $ ./autogen.sh && make
I am going to run ./configure with no arguments - if you wish
to pass any to it, please specify them on the ./autogen.sh command line.
processing .
Running libtoolize...
Running aclocal-1.8  ...
/usr/share/aclocal/pkg.m4:5: warning: underquoted definition of PKG_CHECK_MODULE S
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending%20aclocal](http://sources.redhat.com/automake/automake.html#Extending%20aclocal)
/usr/share/aclocal/nspr.m4:8: warning: underquoted definition of AM_PATH_NSPR
Running autoheader...
Running automake-1.8 --gnu  ...
Running autoconf ...
Running ./configure --enable-maintainer-mode --enable-compile-warnings ...
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
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
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
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
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for pkg-config... /usr/bin/pkg-config
checking which mozilla to use... mozilla
checking for mozilla-gtkmozembed >= 1.6 mozilla-xpcom >= 1.6... yes
checking MOZILLA_COMPONENT_CFLAGS... -I/usr/include/mozilla/gtkembedmoz -I/usr/i nclude/mozilla/xpcom -I/usr/include/mozilla/string -I/usr/include/mozilla/nspr
checking MOZILLA_COMPONENT_LIBS... -L/usr/lib/mozilla -lgtkembedmoz -lxpcom -lpl ds4 -lplc4 -lnspr4 -ldl -lc -lpthread
checking for compiler -fshort-wchar option... yes
checking whether nsIFilePicker methods expect nsAString&... no
checking whether nsIMIMEInfo methods expect nsAString&... no
checking for nsIXULChromeRegistry API... yes
checking for /usr/include/mozilla/chrome/nsIChromeRegistrySea.h... no
checking for gtk+-2.0 >= 2.2 mozilla-gtkmozembed... yes
checking LIBGECKOGLUE_CFLAGS... -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk -2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1. 0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include - I/usr/include/mozilla/gtkembedmoz -I/usr/include/mozilla/xpcom -I/usr/include/mo zilla/string -I/usr/include/mozilla/nspr
checking LIBGECKOGLUE_LIBS... -Wl,--export-dynamic -L/usr/lib/mozilla -lgtk-x11- 2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lp ango-1.0 -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -lgtkembedmoz -lxpcom -lplds4 -l plc4 -lnspr4 -ldl -lc -lpthread
checking for gtk-sharp gecko-sharp gnome-sharp dbus-sharp gconf-sharp... Package  gecko-sharp was not found in the pkg-config search path.
Perhaps you should add the directory containing `gecko-sharp.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gecko-sharp' found

configure: error: Library requirements (gtk-sharp gecko-sharp gnome-sharp dbus-s harp gconf-sharp) not met; consider adjusting the PKG_CONFIG_PATH environment va riable if your libraries are in a nonstandard prefix so pkg-config can find them .
You have new mail in /var/mail/bubba
bubba@bubbashack:~/cvs/beagle $
```

And then I get ...

```
bubba@bubbashack:~/cvs/beagle $ beagled
bash: beagled: command not found

```

Any suggestions?

---

### Post by randy on 2004-11-12
In order to build beagle you'll need to build the mozilla-dev package so you have the header files installed.

---

### Post by shoelessmike on 2004-11-13
I think mozilla-dev is installed ... according to synaptic, leastways.

---

### Post by randy on 2004-11-13
From the your error message you'll need to install gecko-sharp.  I can't remember if there's a package for this or not.  You may need to install it from source.

---

### Post by HiddenWolf on 2004-11-13
sorry, but isn't beagle either a type of dog, or a nasty virus? :-)

---

### Post by julien on 2004-11-13
IIRC, gecko-sharp should be the libgecko-cil package.

---

### Post by shoelessmike on 2004-11-13
FYI: 
Beagle is a search tool, see [here](http://www.gnome.org/projects/beagle/). Installed libgecko-cil and am looking for libgecko-sharp. So far, nothing   :-?

---

### Post by rwabel on 2005-01-09
I'm on hoary and installed it also by following the wiki. 
My problem is the beagle daemon:
INFO: Starting Beagle Daemon (version 0.0.4)
DEBUG: Command Line: /usr/local/lib/beagle/BeagleDaemon.exe --fg --debug
FATAL: Could not set extended attributes on a file in your home directory.  See [http://www.beaglewiki.org/index.php/Enable%20Extended%20Attributes](http://www.beaglewiki.org/index.php/Enable%20Extended%20Attributes) for more information.

I've then read on the following homepage that if having reisferfs one need to adapt the kernel. But in is that really true? In the wiki the inotify can be skipped when having hoary.

Anyone has a solution to that?

---

### Post by vificunero on 2005-02-17
[QUOTE=shoelessmike]Figured as long as beagle problems were here ...
I've been working on installing beagle and got to just about the end. 


And then I get ...



Any suggestions?[/QUOTE]

I have the same error. Did anyone install it?

---

