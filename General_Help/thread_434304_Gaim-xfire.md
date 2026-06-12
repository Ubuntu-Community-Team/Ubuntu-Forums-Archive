---
title: "Gaim-xfire"
date: 2007-05-05
forum: General Help
---

### Post by nanonomic on 2007-05-05
yeah i have a lot of friends that only use Xfire...i followed Indreks instructions. but it didnt work. console output:

pencilpoint@russipc1:~/gaim-xfire-0.6.0$ sudo ./configure --with-gaim=/usr/lib/pkgconfig/ --prefix=/usr && make && make install
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for SSL... yes
checking for GAIM... yes
checking for GAIM version... 2.0.x
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... yes (version 2.12.11)
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
./configure: line 5654: ./po/POTFILES.in: No such file or directory
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
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
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating pixmaps/Makefile
config.status: creating pre_config.h
config.status: executing default-1 commands
config.status: executing default-2 commands

Configuration complete

Debugging enabled..............: no
Using gaim version.............: 2.0
Gaim package prefix............: /usr
Gaim package libdir............: /usr/lib
Install prefix.................: /usr
Install libdir.................: /usr/lib
Gaim lib dir detected..........: Yes


Type make to compile

Make sure you copy data/gfire_games.xml to /home/pencilpoint/.gaim/

/bin/sed 's/#define PACKAGE/#define GFIRE_PACKAGE/g' pre_config.h > gfire_config.h
make  all-recursive
make[1]: Entering directory `/home/pencilpoint/gaim-xfire-0.6.0'
Making all in src
make[2]: Entering directory `/home/pencilpoint/gaim-xfire-0.6.0/src'
/bin/bash ../libtool --silent --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..  -DLIBDIR=\"/usr/lib/gaim/\"      -DDATADIR=\"/usr/share\"        -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I/usr/include/gaim -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include                    -Wall -g3 -c gfire.c
gfire.c: In function 'gfire_login':
gfire.c:353: warning: passing argument 2 of 'gaim_proxy_connect' from incompatible pointer type
gfire.c:353: warning: passing argument 3 of 'gaim_proxy_connect' makes pointer from integer without a cast
gfire.c:353: warning: passing argument 4 of 'gaim_proxy_connect' makes integer from pointer without a cast
gfire.c:353: warning: passing argument 5 of 'gaim_proxy_connect' from incompatible pointer type
gfire.c:353: error: too few arguments to function 'gaim_proxy_connect'
gfire.c: At top level:
gfire.c:1498: warning: initialization from incompatible pointer type
make[2]: *** [gfire.lo] Error 1
make[2]: Leaving directory `/home/pencilpoint/gaim-xfire-0.6.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/pencilpoint/gaim-xfire-0.6.0'
make: *** [all-recursive-am] Error 2
pencilpoint@russipc1:~/gaim-xfire-0.6.0$ 








any ideas?

---

