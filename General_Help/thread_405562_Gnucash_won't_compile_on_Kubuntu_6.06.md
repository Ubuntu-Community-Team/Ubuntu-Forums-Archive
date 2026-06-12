---
title: "Gnucash won't compile on Kubuntu 6.06"
date: 2007-04-09
forum: General Help
---

### Post by The Iron Curtain on 2007-04-09
Hello,

I'm trying to install the latest version of GNUCash (2.05) on my x86 Kubuntu 6.06
The one in the repos is v1.8, and I have files that need the latest version to work

So, I got the source, did the ./configure, went through dependancy hell, and now I've hit a wall. I don't know what to do. 

Here is the output from my terminal:
```

dfoer@dfoer-desktop:/opt/gnucash-2.0.5$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for catalogs to be installed...  ca cs da de el en_GB es_NI es eu fr hu it ja nb ne nl pl pt_BR pt ro ru rw sk sv ta tr uk zh_CN zh_TW
checking for a BSD-compatible install... /usr/bin/install -c
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
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
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
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
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
checking whether a statically linked program can dlopen itself... no
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for library containing strerror... none required
checking whether byte ordering is bigendian... no
checking whether make sets $(MAKE)... (cached) yes
checking whether ln -s works... yes
checking for ANSI C header files... (cached) yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking sys/times.h usability... yes
checking sys/times.h presence... yes
checking for sys/times.h... yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking for stpcpy... yes
checking for memcpy... yes
checking for timegm... yes
checking for towupper... yes
checking for setenv... yes
checking for the tm_gmtoff member of struct tm... yes
checking if scanf supports %lld conversions... yes
checking ltdl.h usability... yes
checking ltdl.h presence... yes
checking for ltdl.h... yes
checking X11/Xlib.h usability... no
checking X11/Xlib.h presence... no
checking for X11/Xlib.h... no
checking glob.h usability... yes
checking glob.h presence... yes
checking for glob.h... yes
checking for chown... yes
checking for gethostname... yes
checking for getppid... yes
checking for getuid... yes
checking for gettimeofday... yes
checking for gmtime_r... yes
checking for gethostid... yes
checking for link... yes
checking for pkg-config... /usr/bin/pkg-config
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GLIB - version >= 2.4.0... yes (version 2.10.3)
checking for GLIB - version >= 2.6.0... yes
checking for GLIB - version >= 2.9.0... yes
checking for untested GLIB versions (glib >= 2.11.0)... no
checking for dlfcn.h... (cached) yes
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking utmp.h usability... yes
checking utmp.h presence... yes
checking for utmp.h... yes
checking for locale.h... (cached) yes
checking mcheck.h usability... yes
checking mcheck.h presence... yes
checking for mcheck.h... yes
checking for unistd.h... (cached) yes
checking wctype.h usability... yes
checking wctype.h presence... yes
checking for wctype.h... yes
checking for dlsym... no
checking for dlsym in -ldl... yes
checking for dlerror... yes
checking for darwin... no
checking for qt_null in -lqthreads... yes
checking for main in -ltermcap... yes
checking for main in -lreadline... yes
checking for guile-config... yes
checking whether guile-config works... yes
checking for sin in -lm... yes
checking for guile libraries... -lguile -lguile-ltdl -lqthreads -lpthread -lcrypt -lm
checking for guile headers...
checking whether guile works... yes
checking for guile... /usr/bin/guile
checking for guile - 1.6.0 <= version < 99.99.99... yes: 1.6.7
checking for guile - 1.8.0 <= version < 99.99.99... no: 1.6.7
checking for g-wrap-config... /usr/bin/g-wrap-config
checking for g-wrap - version >= 1.3.3... yes
checking for g-wrap compile args... -std=gnu99
checking for g-wrap link args... -lgwrap-guile-runtime -lgwrap-core-runtime -lguile -lguile-ltdl -lqthreads -lpthread -lcrypt -lm -lffi
checking for g-wrap module directory... /usr/share/guile/site
checking g-wrap-wct.h usability... yes
checking g-wrap-wct.h presence... yes
checking for g-wrap-wct.h... yes
checking for (g-wrap) guile module... yes
checking for (g-wrap gw-glib-spec) guile module... yes
checking for SLIB support... yes
checking for (g-wrap gw-standard) guile module... no
checking for (g-wrap gw standard) guile module... yes
checking if guile long_long is at least as big as gint64... yes
checking for scm_long_long2num in -lguile... yes
checking if unsigned long is at least as big as guint32... yes
checking if guile needs our copy of srfi-1... no
checking if guile needs our copy of srfi-11... no
checking if guile needs our copy of srfi-19... no
checking if guile needs our copy of srfi-2... no
checking if guile needs our copy of srfi-8... no
checking if guile needs our copy of srfi-9... no
checking if guile needs our copy of (guile www)... checking for guile... (cached) /usr/bin/guile
checking for guile-config... /usr/bin/guile-config
checking for guile-tools... /usr/bin/guile-tools
checking if (www main) is available... no
checking for gconf-2.0 >= "2.0"... Package gconf-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gconf-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gconf-2.0' found
configure: error: Library requirements (gconf-2.0 >= "2.0") not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
dfoer@dfoer-desktop:/opt/gnucash-2.0.5$

```

I don't understand the error. I know when to get a missing library, but this one just confuses me.

Thank you for your help

---

### Post by WiseElben on 2007-04-09
You probably need to install these packages:

```

$ sudo aptitude install gconf2 libgconf2-dev

```

The gconf2 in the repos is version 2.16, which satisfies >= "2.0" condition.

---

### Post by The Iron Curtain on 2007-04-09
Thank you! I ran ./configure again, and I have this error. I'm looking in adept's listing of the repos and I'm not sure what to get

```

checking what warning flags to pass to the C compiler... -Wall -Wunused -Wmissing-prototypes -Wmissing-declarations
checking what language compliance flags to pass to the C compiler...
checking for gtk+-2.0 >= 2.4... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.4) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
dfoer@dfoer-desktop:/opt/gnucash-2.0.5$                                                   

```

Thank you!

EDIT: nevermind, I found the file. It seems, I forgot to install all the dev files, mostly because that seems to solve my problems

---

### Post by The Iron Curtain on 2007-04-10
Huzzah! It works! Thank you very much for your help!

---

