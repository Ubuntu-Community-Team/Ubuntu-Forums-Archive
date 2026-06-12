---
title: "Installing tar.gz driving me nuts, (make)-errors.."
date: 2007-06-19
forum: General Help
---

### Post by rockstar82 on 2007-06-19
I downloaded this [tar.gz-file](http://www.kde-look.org/content/show.php/QtCurve+%28KDE4%2C+KDE3%2C+%26+Gtk2+Theme%29?content=40492), but i have serious issues installing it. It worked a couple of weeks ago, but it refuses now as i reinstalled Kubuntu.

I have installed all essentials needed for configuring, see the output below.

./configure
```

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
/bin/bash: /home/dego/nerladdat/tar,: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wnon-virtual-dtor... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -O0... yes
checking whether g++ supports -Wl,--no-undefined... yes
checking whether g++ supports -Wl,--allow-shlib-undefined... yes
not using lib directory suffix
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
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
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "F77" to libtool
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking if C++ programs can be compiled... yes
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... yes
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking sys/bitypes.h usability... yes
checking sys/bitypes.h presence... yes
checking for sys/bitypes.h... yes
checking for poll in -lpoll... no
checking Carbon/Carbon.h usability... no
checking Carbon/Carbon.h presence... no
checking for Carbon/Carbon.h... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking for res_init... yes
checking if res_init needs custom prototype... no
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for short... yes
checking size of short... 2
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for dlopen in -ldl... (cached) yes
checking for shl_unload in -ldld... no
checking for size_t... yes
checking size of size_t... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking sizeof size_t == sizeof unsigned long... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... libraries /usr/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for perl... /usr/bin/perl
checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... libraries /usr/lib, headers /usr/include/kde
checking if UIC has KDE plugins available... yes
checking for KDE paths... defaults
checking for dcopidl... /usr/bin/dcopidl
checking for dcopidl2cpp... /usr/bin/dcopidl2cpp
checking for mcopidl... /usr/bin/mcopidl
checking for artsc-config... /usr/bin/artsc-config
checking for meinproc... /usr/bin/meinproc
checking for kconfig_compiler... /usr/bin/kconfig_compiler
checking for dcopidlng... /usr/bin/dcopidlng
checking for makekdewidgets... /usr/bin/makekdewidgets
checking for xmllint... /usr/bin/xmllint
checking for setenv... yes
checking for unsetenv... yes
checking if admin should be compiled... no
checking if kde should be compiled... yes
configure: creating ./config.status
wrong input (flag != 4) at admin/conf.change.pl line 117, <> line 1229.
config.status: creating Makefile
config.status: creating kde/Makefile
config.status: creating kde/config/Makefile
config.status: creating config.h
config.status: executing depfiles commands

Good - your configure finished. Start make now
```

But when it comes to _make_, it does not work. The output is in swedish, i tried to translate it. 

make
```
Makefile:851: warning: something about "clean-bcheck"
Makefile:817: warning: something about "clean-bcheck"
Makefile:856: warning: something about "bcheck-am"
Makefile:822: warning: something about "bcheck-am"
cd . && make -f admin/Makefile.common configure.in
make[1]: Entering directory `/QtCurve-KDE3-0.52'
*** Creating configure.files
make[1]: Leaving directory `/QtCurve-KDE3-0.52'
cd . && aclocal-1.9
/bin/bash: aclocal-1.9: command not found
make: *** [aclocal.m4] error 127
```

What does this mean? I tried re-downloading and re-configure several times, but its always the same error.

---

### Post by Beefeater on 2007-06-19
Well some of us can read Swedish ..
Have you installed automake?

---

### Post by rockstar82 on 2007-06-19
> **Beefeater said:**
> Well some of us can read Swedish ..
Have you installed automake?

This is the original output in swedish, a little cryptic.

```
Makefile:851: varning: åsidosätter kommandon för målet "clean-bcheck"
Makefile:817: varning: bortser från gamla kommandon för målet "clean-bcheck"
Makefile:856: varning: åsidosätter kommandon för målet "bcheck-am"
Makefile:822: varning: bortser från gamla kommandon för målet "bcheck-am"
cd . && make -f admin/Makefile.common configure.in
make[1]: Entering directory `/QtCurve-KDE3-0.52'
*** Creating configure.files
make[1]: Leaving directory `QtCurve-KDE3-0.52'
cd . && aclocal-1.9
/bin/bash: aclocal-1.9: kommandot hittades inte
make: *** [aclocal.m4] Fel 127
```

I have installed automake, and in the desperation i also installed (for ./configure):
build-essentials
libqt3-mt-dev
kdelibs-dev
autoconf.

---

### Post by Mr. C. on 2007-06-19
You need autoconfig and automake packages.

MrC

---

### Post by Beefeater on 2007-06-19
> **rockstar82 said:**
> This is the original output in swedish, a little cryptic.

```
Makefile:851: varning: åsidosätter kommandon för målet "clean-bcheck"
Makefile:817: varning: bortser från gamla kommandon för målet "clean-bcheck"
Makefile:856: varning: åsidosätter kommandon för målet "bcheck-am"
Makefile:822: varning: bortser från gamla kommandon för målet "bcheck-am"
cd . && make -f admin/Makefile.common configure.in
make[1]: Entering directory `/QtCurve-KDE3-0.52'
*** Creating configure.files
make[1]: Leaving directory `QtCurve-KDE3-0.52'
cd . && aclocal-1.9
/bin/bash: aclocal-1.9: kommandot hittades inte
make: *** [aclocal.m4] Fel 127
```

I have installed automake, and in the desperation i also installed (for ./configure):
build-essentials
libqt3-mt-dev
kdelibs-dev
autoconf.

hmm .. and you are sure you installed automake1.9?
apt-file search aclocal-1.9

---

### Post by rockstar82 on 2007-06-20
> **Beefeater said:**
> hmm .. and you are sure you installed automake1.9?
apt-file search aclocal-1.9

Hm, i don't know, i installed *#apt-get install automake*. I am a bit unsure how to use it, should i type *automake* (didn't work) instead of *make*?

However it does work now, i have no idea what i did wrong? :-k

Thanks alot for helping out!

---

### Post by Beefeater on 2007-06-20
> **rockstar82 said:**
> Hm, i don't know, i installed *#apt-get install automake*. I am a bit unsure how to use it, should i type *automake* (didn't work) instead of *make*?

However it does work now, i have no idea what i did wrong? :-k

Thanks alot for helping out!

If you do
apt-get install automake
you get v 1.10 and with that aclocal-1.10 instead of 1.9

But I'm happy that it worked for you.

---

