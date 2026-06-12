---
title: "[SOLVED] Plugin for Pidgin"
date: 2008-01-14
forum: General Help
---

### Post by nkobel003 on 2008-01-14
Hi,
I have been getting IM spam, and a place told me to get the bot-sentry plugin for Pidgin.  I got the tar.bz2 file, but I don't know what to do with it.  I got the plugin from here:
[http://sourceforge.net/projects/pidgin-bs/](http://sourceforge.net/projects/pidgin-bs/)
Any suggestions?

---

### Post by SOULRiDER on 2008-01-14
You have to compile it.

Install the necesary tools:
```
sudo aptitude install build-essential pidgin-dev checkinstall
```
Exctract the file, go tot he directory and run these commands.
```
./configure
make
sudo checkinstall
```

---

### Post by SOULRiDER on 2008-01-14
Theres also a package called pidgin-plugin-pack: [http://packages.ubuntu.com/gutsy/net/pidgin-plugin-pack](http://packages.ubuntu.com/gutsy/net/pidgin-plugin-pack)

It doesnt birng that plugin but it might have other useful plugins.

---

### Post by nkobel003 on 2008-01-15
THANK YOU!
my troubles are at ease.

---

### Post by SOULRiDER on 2008-01-15
Hey, no problem!
Could you please mark the thread as solved?
Take a look at this link on how to do it, its really simple: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by elamericano on 2008-02-15
For the 1.1.0, the installation didn't work. I had to copy the plugin files to /usr/lib/purple-2/

```
sudo cp /usr/local/lib/bot-sentry.* /usr/lib/purple-2/.
```

It appears to be working. If I go a whole day without getting IM spam, then I'll know.

---

### Post by karlo on 2008-03-16
> **elamericano said:**
> For the 1.1.0, the installation didn't work. I had to copy the plugin files to /usr/lib/purple-2/

```
sudo cp /usr/local/lib/bot-sentry.* /usr/lib/purple-2/.
```

It appears to be working. If I go a whole day without getting IM spam, then I'll know.

**THANK YOU!**

Is this corrent? Well, how can I remove the unnecessary and temporary files? And can I remove the pidgin-dev files? Files that are needed to compile pidgin files?

At the same time, can I distribute the .deb file, since it's every confusing to make that file, why not make that file public so that the installation will be hassle free?

```
karlo@karlo-laptop:~/Desktop$ sudo apt-get install libqt3-mt curl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt3-mt is already the newest version.
libqt3-mt set to manual installed.
The following NEW packages will be installed:
  curl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 175kB of archives.
After unpacking 291kB of additional disk space will be used.
Get:1 http://tw.archive.ubuntu.com gutsy/main curl 7.16.4-2ubuntu1 [175kB]
Fetched 175kB in 4s (39.2kB/s)          
Selecting previously deselected package curl.
(Reading database ... 136923 files and directories currently installed.)
Unpacking curl (from .../curl_7.16.4-2ubuntu1_i386.deb) ...
Setting up curl (7.16.4-2ubuntu1) ...
karlo@karlo-laptop:~/Desktop$ clear

karlo@karlo-laptop:~/Desktop$ cd /home/karlo/Desktop/bot-sentry-1.1.0
karlo@karlo-laptop:~/Desktop/bot-sentry-1.1.0$ ls
aclocal.m4    configure.ac         intltool-update.in   nsis
AUTHORS       COPYING              ltmain.sh            po
ChangeLog     depcomp              Makefile.am          README
config.guess  INSTALL              Makefile.in          README.mingw
config.h.in   install-sh           mingw-purple-dev.sh  src
config.sub    intltool-extract.in  missing
configure     intltool-merge.in    NEWS
karlo@karlo-laptop:~/Desktop/bot-sentry-1.1.0$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
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
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for intltool >= 0.35.0... 0.35.0 found
checking for perl... /usr/bin/perl
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for head... /usr/bin/head
checking for makensis... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.15.0... yes
checking for purple... yes
checking purple_CFLAGS... -I/usr/include/libpurple -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking purple_LIBS... -lpurple -lglib-2.0  
checking PURPLE_VERSION... 2.2.1
checking PURPLE_MAJOR_VERSION... 2
checking locale_CPPFLAGS... -DLOCALEDIR=\"$(prefix)/$(DATADIRNAME)/locale\"
checking for library containing g_get_current_time... none required
checking for library containing purple_account_get_connection... none required
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
checking glib.h usability... yes
checking glib.h presence... yes
checking for glib.h... yes
checking plugin.h usability... yes
checking plugin.h presence... yes
checking for plugin.h... yes
checking for version.h... yes
checking util.h usability... yes
checking util.h presence... yes
checking for util.h... yes
checking debug.h usability... yes
checking debug.h presence... yes
checking for debug.h... yes
checking account.h usability... yes
checking account.h presence... yes
checking for account.h... yes
checking accountopt.h usability... yes
checking accountopt.h presence... yes
checking for accountopt.h... yes
checking privacy.h usability... yes
checking privacy.h presence... yes
checking for privacy.h... yes
checking for an ANSI C-conforming const... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating po/Makefile.in
config.status: creating po/Makevars
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

bot-sentry 1.1.0

configured plugin installation directory... : /usr/local/lib
configured locale installation directory... : /usr/local/share/locale

configure complete, now type 'make'

karlo@karlo-laptop:~/Desktop/bot-sentry-1.1.0$ make
make  all-recursive
make[1]: Entering directory `/home/karlo/Desktop/bot-sentry-1.1.0'
Making all in po
make[2]: Entering directory `/home/karlo/Desktop/bot-sentry-1.1.0/po'
file=`echo ar | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file ar.po
file=`echo cs | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file cs.po
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file de.po
file=`echo es | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file es.po
file=`echo it | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file it.po
file=`echo no | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file no.po
make[2]: Leaving directory `/home/karlo/Desktop/bot-sentry-1.1.0/po'
make[2]: Entering directory `/home/karlo/Desktop/bot-sentry-1.1.0'
depbase=`echo src/bot-sentry.lo | sed 's|[^/]*$|.deps/&|;s|\.lo$||'`;\
        /bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -DLOCALEDIR=\"/usr/local/share/locale\" -I/usr/include/libpurple -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -g -O2 -MT src/bot-sentry.lo -MD -MP -MF $depbase.Tpo -c -o src/bot-sentry.lo src/bot-sentry.c &&\
        mv -f $depbase.Tpo $depbase.Plo
mkdir src/.libs
 gcc -DHAVE_CONFIG_H -I. -DLOCALEDIR=\"/usr/local/share/locale\" -I/usr/include/libpurple -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -g -O2 -MT src/bot-sentry.lo -MD -MP -MF src/.deps/bot-sentry.Tpo -c src/bot-sentry.c  -fPIC -DPIC -o src/.libs/bot-sentry.o
/bin/bash ./libtool --tag=CC   --mode=link gcc  -g -O2 -module -avoid-version -no-undefined -lpurple -lglib-2.0    -o src/bot-sentry.la -rpath /usr/local/lib src/bot-sentry.lo  
gcc -shared  src/.libs/bot-sentry.o  -lpurple /usr/lib/libglib-2.0.so  -Wl,-soname -Wl,bot-sentry.so -o src/.libs/bot-sentry.so
creating src/bot-sentry.la
(cd src/.libs && rm -f bot-sentry.la && ln -s ../bot-sentry.la bot-sentry.la)
make[2]: Leaving directory `/home/karlo/Desktop/bot-sentry-1.1.0'
make[1]: Leaving directory `/home/karlo/Desktop/bot-sentry-1.1.0'
karlo@karlo-laptop:~/Desktop/bot-sentry-1.1.0$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@karlo-laptop ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ bot-sentry ]
3 -  Version: [ 1.1.0 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ bot-sentry-1.1.0 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Making install in po
make[1]: Entering directory `/home/karlo/Desktop/bot-sentry-1.1.0/po'
/bin/sh /home/karlo/Desktop/bot-sentry-1.1.0/install-sh -d /usr/local/share/locale
if test -n " ar cs de es it no"; then \
          linguas=" ar cs de es it no"; \
        else \
          linguas=""; \
        fi; \
        for lang in $linguas; do \
          dir=/usr/local/share/locale/$lang/LC_MESSAGES; \
          /bin/sh /home/karlo/Desktop/bot-sentry-1.1.0/install-sh -d $dir; \
          if test -r $lang.gmo; then \
            /usr/bin/install -c -m 644 $lang.gmo $dir/bot-sentry.mo; \
            echo "installing $lang.gmo as $dir/bot-sentry.mo"; \
          else \
            /usr/bin/install -c -m 644 ./$lang.gmo $dir/bot-sentry.mo; \
            echo "installing ./$lang.gmo as" \
                 "$dir/bot-sentry.mo"; \
          fi; \
          if test -r $lang.gmo.m; then \
            /usr/bin/install -c -m 644 $lang.gmo.m $dir/bot-sentry.mo.m; \
            echo "installing $lang.gmo.m as $dir/bot-sentry.mo.m"; \
          else \
            if test -r ./$lang.gmo.m ; then \
              /usr/bin/install -c -m 644 ./$lang.gmo.m \
                $dir/bot-sentry.mo.m; \
              echo "installing ./$lang.gmo.m as" \
                   "$dir/bot-sentry.mo.m"; \
            else \
              true; \
            fi; \
          fi; \
        done
/usr/bin/install: setting permissions for `/usr/local/share/locale/ar/LC_MESSAGES/bot-sentry.mo': No such file or directory
installing ar.gmo as /usr/local/share/locale/ar/LC_MESSAGES/bot-sentry.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/cs/LC_MESSAGES/bot-sentry.mo': No such file or directory
installing cs.gmo as /usr/local/share/locale/cs/LC_MESSAGES/bot-sentry.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/de/LC_MESSAGES/bot-sentry.mo': No such file or directory
installing de.gmo as /usr/local/share/locale/de/LC_MESSAGES/bot-sentry.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/es/LC_MESSAGES/bot-sentry.mo': No such file or directory
installing es.gmo as /usr/local/share/locale/es/LC_MESSAGES/bot-sentry.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/it/LC_MESSAGES/bot-sentry.mo': No such file or directory
installing it.gmo as /usr/local/share/locale/it/LC_MESSAGES/bot-sentry.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/no/LC_MESSAGES/bot-sentry.mo': No such file or directory
installing no.gmo as /usr/local/share/locale/no/LC_MESSAGES/bot-sentry.mo
make[1]: Leaving directory `/home/karlo/Desktop/bot-sentry-1.1.0/po'
make[1]: Entering directory `/home/karlo/Desktop/bot-sentry-1.1.0'
make[2]: Entering directory `/home/karlo/Desktop/bot-sentry-1.1.0'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ./libtool --mode=install /usr/bin/install -c  'src/bot-sentry.la' '/usr/local/lib/bot-sentry.la'
/usr/bin/install -c src/.libs/bot-sentry.so /usr/local/lib/bot-sentry.so
/usr/bin/install: setting permissions for `/usr/local/lib/bot-sentry.so': No such file or directory
/usr/bin/install -c src/.libs/bot-sentry.lai /usr/local/lib/bot-sentry.la
/usr/bin/install: setting permissions for `/usr/local/lib/bot-sentry.la': No such file or directory
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make  install-exec-hook
make[3]: Entering directory `/home/karlo/Desktop/bot-sentry-1.1.0'
rm -f /usr/local/lib/libbot-challenger.*
rm -f /usr/local/lib/libgaim-bs.*
rm -f /usr/local/lib/libpidgin-bs.*
make[3]: Leaving directory `/home/karlo/Desktop/bot-sentry-1.1.0'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/karlo/Desktop/bot-sentry-1.1.0'
make[1]: Leaving directory `/home/karlo/Desktop/bot-sentry-1.1.0'

======================== Installation successful ==========================

Copying documentation directory...
./
./README
./NEWS
./README.mingw
./AUTHORS
./INSTALL
./ChangeLog
./COPYING
grep: /var/tmp/cVXLfGgYSlBjokAemlJVI/newfile: No such file or directory

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Erasing temporary files...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/karlo/Desktop/bot-sentry-1.1.0/bot-sentry_1.1.0-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r bot-sentry

**********************************************************************
```

Finally:

```
karlo@karlo-laptop:~/Desktop/bot-sentry-1.1.0$ sudo mv /usr/local/lib/bot-sentry.* /usr/lib/purple-2/.
```

---

### Post by blackwatch on 2008-03-21
Thanks for this information, guys. I needed to add that and with the instructions, pulled it off quickly. 

Thanks again!

---

### Post by karlo on 2008-03-22
> **blackwatch said:**
> Thanks for this information, guys. I needed to add that and with the instructions, pulled it off quickly. 

Thanks again!

Oh yeah, did you noticed? No one is flooding you anymore, right? :)

---

### Post by cross157 on 2008-05-01
Thank you for this information.

I have Bot Sentry installed and "working" BUT every time Bot Sentry catches a spam IM, it pops up the IM window anyway. It doesn't make sense to me, its a pop up blocker that displays pop ups, wtf?

---

### Post by ekravche on 2008-05-08
> **SOULRiDER said:**
> You have to compile it.

Install the necesary tools:
```
sudo aptitude install build-essential pidgin-dev checkinstall
```
Exctract the file, go tot he directory and run these commands.
```
./configure
make
sudo checkinstall
```


installing the package pidgin-dev did it for me. I removed it afterwards because ubuntu said that it was unsafe to install this package to begin with.

---

### Post by spadewarrior on 2008-07-24
I'm having trouble compiling bot sentry. Here's the output:
```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
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
checking for prefix by checking for pidgin... /usr/bin/pidgin
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking the maximum length of command line arguments... 98304
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
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
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for intltool >= 0.40.0... 0.37.1 found
configure: error: Your intltool is too old.  You need intltool 0.40.0 or later.
```

I installed intltool from synaptic but it didn't help.

Any ideas?

---

