---
title: "&quot;Make&quot; command doesn't work"
date: 2006-10-30
forum: General Help
---

### Post by massivevoid on 2006-10-30
And I have the "build-essential" installed, but it still won't work.

```
william@william-laptop:~/Desktop/fluxbox-1.0rc2$ make
make: *** No targets specified and no makefile found.  Stop.
```

---

### Post by MyAnda on 2006-10-30
is there a Makefile in the directory? have you run ./configure ?

---

### Post by massivevoid on 2006-10-30
There is a Makefile in the dir (Makefile.am, Makefile.in ?) and I run the ./configure, too.

No go.

---

### Post by Julolidine on 2006-10-30
what did you type?  Just make?

or sudo make install?

or sudo make?

If theres a readme, typically they will have the commands you need to issue sans sudo.

---

### Post by ~LoKe on 2006-10-30
Give us the directory listing, please. =)
check for a autogen.sh, as well.

---

### Post by massivevoid on 2006-10-30
I typed "make".

Here is the read me

```
This is a development version of Fluxbox.

Fluxbox is a fork of the original Blackbox 0.61.1 sourcecode with
different goals.

Read NEWS to see whats new in this release.

For copyright information see COPYING

For more information and extensive documentation go to:
  http://fluxbox.org/version-0.9.php


Compile and Install:

  $ ./configure
  $ make
  and then as root
  # make install

Configuration options:

  For KDE slitsupport (default): (Allows kde tray icons to be placed in systray inside the toolbar)
    ./configure --enable-kde

  For Gnome support (default):
    ./configure --enable-gnome

  Use ./configure --help to see the full list of options



For former blackbox users:

 - You can use your old blackbox configuration file too. Just copy
   .blackboxrc to ~/.fluxbox/init . The same goes for menu file.

 - You can also use the Blackbox themes in Fluxbox. Fluxbox has a few
   extra styleoption for the tabs but they don't have to be specified.

 - The keys file is no longer compatible with bbkeys. There's a
   convertkeys script at http://fluxbox.sourceforge.net/ that will
   convert the bbkeys format to the fluxbox format.


A few extra notes about the new features:

 - To disable tabs and/or iconbar just change it in configure menu.

 - To work with tabs, use the third mouse button to drag a tab to
   another tab.  This will group the two windows together.

 - With 'Sloppy Window Grouping' turned on (in your configure menu),
   you can drop the tabs anywhere on the target window to group
   windows together.

 - The 'Maximize over Slit' option means that maximized windows will not
   stop at the outside border of the slit, and will instead cover it.

 - In the init file, the session.screen0.rootCommand: option will
   override the rootCommand option in a theme, keeping your background
   the same, no matter what the theme says it should be.


Thanks:

  Blackbox team

  aleczapka, skarin, Perc, xfs, skypher and skywarper for bugtesting.

  skypher of openprojects for bugtesting and providing fluxbox with
    themes: Clean CleanColor Makro, Carbondioxide and MerleyKay.

  People at #fluxbox on the irc.freenode.net irc-network.

  And all the people who sent bugfixes/patches.


This software is OSI Certified Open Source Software.
OSI Certified is a certification mark of the Open Source Initiative.

```

And there is no "autogen.sh"

Here is what is inside the folder:

acinclude.m4, aclocal.m4, AUTHORS, ChangeLog, config.guess, config.h.in, config.log, config.sub, configure, configure.in, COPYING, depcomp, INSTALL, install-sh, libtool, Itconfig, Itmain.sh, Makefile.am, Makefile.in, missing, mkinstalldirs, NEWS, README, TODO, version.h.in

Also there are a couple of folders.

---

### Post by ~LoKe on 2006-10-30
```
sudo ./configure && make && sudo make install
```

---

### Post by massivevoid on 2006-10-30
Hmm, don't know if that worked.

```
william@william-laptop:~/Desktop/fluxbox-1.0rc2$ sudo ./configure && make && sudo make install
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/william/Desktop/fluxbox-1.0rc2/missing: Unknown `--run' option
Try `/home/william/Desktop/fluxbox-1.0rc2/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
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
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for correct ltmain.sh version... yes
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
checking for sed... sed
checking for ANSI C header files... (cached) yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking libgen.h usability... yes
checking libgen.h presence... yes
checking for libgen.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking process.h usability... no
checking process.h presence... no
checking for process.h... no
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/signal.h usability... yes
checking sys/signal.h presence... yes
checking for sys/signal.h... yes
checking for sys/stat.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for sys/types.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking iconv.h usability... yes
checking iconv.h presence... yes
checking for iconv.h... yes
checking sstream usability... yes
checking sstream presence... yes
checking for sstream... yes
checking cassert usability... yes
checking cassert presence... yes
checking for cassert... yes
checking cctype usability... yes
checking cctype presence... yes
checking for cctype... yes
checking cerrno usability... yes
checking cerrno presence... yes
checking for cerrno... yes
checking cmath usability... yes
checking cmath presence... yes
checking for cmath... yes
checking cstdarg usability... yes
checking cstdarg presence... yes
checking for cstdarg... yes
checking cstdio usability... yes
checking cstdio presence... yes
checking for cstdio... yes
checking cstdlib usability... yes
checking cstdlib presence... yes
checking for cstdlib... yes
checking cstring usability... yes
checking cstring presence... yes
checking for cstring... yes
checking ctime usability... yes
checking ctime presence... yes
checking for ctime... yes
checking whether time.h and sys/time.h may both be included... yes
checking for basename... yes
checking for getpid... yes
checking for setlocale... yes
checking for sigaction... yes
checking for strcasestr... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for catopen... yes
checking for catgets... yes
checking for catclose... yes
checking for strftime... yes
checking for iconv_open in -liconv... no
checking for libiconv_open in -liconv... no
checking for iconv declaration... no
checking for t_open in -lnsl... no
checking for socket in -lsocket... no
checking for X... no
configure: error: Fluxbox requires the X Window System libraries and headers.

```

---

### Post by Julolidine on 2006-10-30
Well the last line gives it away

"configure: error: Fluxbox requires the configure: error: Fluxbox requires the X Window System libraries and headers. "


I'm not exactly sure which one you need, maybe someone else will.  Perhaps you can simply check the dependencies on the old .deb file, and go from there?

After you resolve that dependency do ./configure again and then make

I tried it on my computer, and it worked fine.  Don't know what I have that you don't though.

---

### Post by Julolidine on 2006-10-30
Ok, it looks like you need
libX11-6

and possibly
libx11-data
libx11-dev

install those packages, and then retry.

---

### Post by Ru$$i@N on 2006-12-27
I know it's too late, but if someone still has a similar problem :

```
sudo apt-get install make
```

I had this problem, i was missing that make file. So the command above (which you type in the terminal :) ) installes the make.

Or go to System->Administration->Synaptic Package Manager   and find "make" on the list. Right-click - "mark to install" - "Apply" (at the top).

Good luck.

---

