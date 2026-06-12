---
title: "Help installing gspeakers from source"
date: 2008-05-08
forum: General Help
---

### Post by StageTech on 2008-05-08
I´m trying to install gspeakers from source. I haven´t had any luck. This the output from when I run ./configure.

> ajk@ubuntu804desktop:~/gspeakers-0.11$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... none
checking for pkg-config... /usr/bin/pkg-config
checking for gtkmm-2.4 libxml-2.0... yes
checking DEPS_CFLAGS... -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/atk-1.0 -I/usr/include/libxml2  
checking DEPS_LIBS... -lgtkmm-2.4 -lgdkmm-2.4 -latkmm-1.6 -lgtk-x11-2.0 -lpangomm-1.4 -lcairomm-1.0 -lglibmm-2.4 -lsigc-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lxml2  
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... none
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
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
checking how to run the C++ preprocessor... g++ -E
checking vector usability... yes
checking vector presence... yes
checking for vector... yes
checking iostream usability... yes
checking iostream presence... yes
checking for iostream... yes
checking fstream usability... yes
checking fstream presence... yes
checking for fstream... yes
checking string usability... yes
checking string presence... yes
checking for string... yes
checking map usability... yes
checking map presence... yes
checking for map... yes
checking iterator usability... yes
checking iterator presence... yes
checking for iterator... yes
checking sstream usability... yes
checking sstream presence... yes
checking for sstream... yes
checking strstream usability... yes
checking strstream presence... yes
checking for strstream... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating xml/Makefile
config.status: creating pixmaps/Makefile
config.status: creating gspeakers.desktop
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
ajk@ubuntu804desktop:~/gspeakers-0.11$ 




Then this is what I get when I run make.

> ajk@ubuntu804desktop:~/gspeakers-0.11$ make
make  all-recursive
make[1]: Entering directory `/home/ajk/gspeakers-0.11'
Making all in src
make[2]: Entering directory `/home/ajk/gspeakers-0.11/src'
source='main.cc' object='main.o' libtool=no \
	depfile='.deps/main.Po' tmpdepfile='.deps/main.TPo' \
	depmode=none /bin/bash ../depcomp \
	g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/atk-1.0 -I/usr/include/libxml2   -Wall -O0 -c -o main.o `test -f 'main.cc' || echo './'`main.cc
/bin/bash: ../depcomp: No such file or directory
make[2]: *** [main.o] Error 127
make[2]: Leaving directory `/home/ajk/gspeakers-0.11/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ajk/gspeakers-0.11'
make: *** [all] Error 2


What do the error messages mean? What am I doing wrong?

---

### Post by joegiampaoli on 2008-06-10
I get the same error

---

