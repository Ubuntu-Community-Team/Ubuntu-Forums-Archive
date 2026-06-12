---
title: "Bored; want to find new ways to explore Ubuntu"
date: 2008-03-15
forum: General Help
---

### Post by Crunchy_Yak on 2008-03-15
Hello,

I am rather new to linux. I just started figuring out how to do some simple commands through the terminal about a month and a half, or two months ago. Now that I've gone through that, I've pretty much customized Ubuntu to how I want it, and I've solved most of the problems that I've had involving my hardware. I would to like to explore ubuntu further. It doesn't really matter what it involves, as long as it expands my knowledge of the operating system. Any ideas?   :p

Thank you in advance. I look forward to being able to contribute to the Ubuntu community.

---

### Post by kerry_s on 2008-03-15
if you just got your system where you want, you should use the live cd to try things, so you don't mess up all you hard work. if you don't want to use live cd, make sure you back up the important things.

you can also, put another install to play with, i suggest using the server install & building up from there, you really get to see what go's into a complete distro when you do it.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

you might also want to try debian, to see where ubuntu gets it's start.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

---

### Post by odiseo77 on 2008-03-15
You could also start compiling and installing program sources that are not available on the repositories. (BTW, I believe this thread goes somewhere else) :)

---

### Post by Crunchy_Yak on 2008-03-15
Thanks! I'll try both of those links, as well as start to intall program sources that are not available through the repositories.

Sorry about placing this thread in the wrong place; you live and learn. ;)

---

### Post by odiseo77 on 2008-03-15
Just as a suggestion, these are a couple of cool programs that are not available in the repositories:

[Guake]("http://www.guake-terminal.org/"): drop down terminal for Gnome similar to yakuake.

[Gyachi]("http://gyachi.sourceforge.net/"): Client for the yahoo IM protocol.

Have fun ;-)

---

### Post by Crunchy_Yak on 2008-03-15
In the 'make' of guake, this is what came up:

make  all-recursive
make[1]: Entering directory `/home/kody/Desktop/guake-0.1'
Making all in src
make[2]: Entering directory `/home/kody/Desktop/guake-0.1/src'
Making all in globalhotkeys
make[3]: Entering directory `/home/kody/Desktop/guake-0.1/src/globalhotkeys'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I/usr/include/python2.5   -g -O2 -MT globalhotkeys.lo -MD -MP -MF .deps/globalhotkeys.Tpo -c -o globalhotkeys.lo globalhotkeys.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/python2.5 -g -O2 -MT globalhotkeys.lo -MD -MP -MF .deps/globalhotkeys.Tpo -c globalhotkeys.c  -fPIC -DPIC -o .libs/globalhotkeys.o
globalhotkeys.c:20:20: error: Python.h: No such file or directory
globalhotkeys.c:32: error: expected specifier-qualifier-list before 'PyObject'
globalhotkeys.c: In function 'caller':
globalhotkeys.c:39: error: 'PyObject' undeclared (first use in this function)
globalhotkeys.c:39: error: (Each undeclared identifier is reported only once
globalhotkeys.c:39: error: for each function it appears in.)
globalhotkeys.c:39: error: 'retval' undeclared (first use in this function)
globalhotkeys.c:41: error: 'PyGILState_STATE' undeclared (first use in this function)
globalhotkeys.c:41: error: expected ';' before 'threadstate'
globalhotkeys.c:43: error: 'threadstate' undeclared (first use in this function)
globalhotkeys.c:56: error: 'CallableObject' has no member named 'callback'
globalhotkeys.c:56: error: 'CallableObject' has no member named 'params'
globalhotkeys.c: At top level:
globalhotkeys.c:64: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
globalhotkeys.c:98: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
globalhotkeys.c:109: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
globalhotkeys.c:116: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'GhMethods'
globalhotkeys.c:125: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'initglobalhotkeys'
make[3]: *** [globalhotkeys.lo] Error 1
make[3]: Leaving directory `/home/kody/Desktop/guake-0.1/src/globalhotkeys'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/kody/Desktop/guake-0.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kody/Desktop/guake-0.1'
make: *** [all] Error 2




This leads me to believe that I need something around the lines of 'python.h' , since it says 'globalhotkeys.c:20:20: error: Python.h: No such file or directory' in the command line. When I type 'aptitude search python.h', this is what comes up:

p   python-hachoir-core                                   - Core of Hachoir framework: parse and edit binary files          
p   python-hachoir-metadata                               - Program to extract metadata using Hachoir library               
p   python-hachoir-parser                                 - Package of Hachoir parsers used to open binary files            
p   python-hachoir-urwid                                  - Binary file explorer using Hachoir and urwid libraries          
p   python-hachoir-wx                                     - wxWidgets GUI for the hachoir binary parser                     
p   python-happydoc                                       - Python Documentation Extraction Tool                            
p   python-happydoc-doc                                   - Python Documentation Extraction Tool Documentation              
p   python-hid                                            - Python wrapper for USB HID access library                       
p   python-hildon                                         - Python bindings for Hildon Framework                            
p   python-hildon-dev                                     - Examples and development files Python Hildon                    
p   python-hippocanvas                                    - Python bindings to hippo-canvas                                 
p   python-hk-classes                                     - Python scripting module for database applications library       
p   python-html5lib                                       - Library for working with HTML5 documents                        
p   python-htmlgen                                        - Python library for the generation of HTML                       
p   python-htmltmpl                                       - Templating engine for separation of code and HTML               
p   python-httplib2                                       - A comprehensive HTTP client library written in python       




Which one do I need?  :S

---

### Post by odiseo77 on 2008-03-15
I think it's the development package for python: ***python-dev***. I've realized when compiling stuff, whenever I see *somelib.h* missing, what I'm missing is the *-dev package for this library. You should also clean the source tree before recompiling (after installing python-dev), with ***make clean*** (or deleting the sources directory and extracting the sources again) :)

---

### Post by Crunchy_Yak on 2008-03-15
Hmmm... After I did the make clean like you said, I went through make again. This time this is what happened:

kody@kody-laptop:~/Desktop/guake-0.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes

checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for a Python interpreter with version >= 2.4.0... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPENDENCIES... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
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
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for catalogs to be installed...  pt_BR
configure: creating ./config.status
config.status: creating Makefile
config.status: creating data/Makefile
config.status: creating data/guake.desktop
config.status: creating data/org.gnome.Guake.service
config.status: creating data/pixmaps/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating src/globalhotkeys/Makefile
config.status: creating src/guake_globals.py
config.status: creating src/guake
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
./config.status: line 1170: po/Makefile: Permission denied



Any ideas why that last line would say 'Makefile: Permission denied'?

---

### Post by Crunchy_Yak on 2008-03-15
Sorry. I went through './configure'. Not 'make'.

---

### Post by odiseo77 on 2008-03-15
I'm not sure, but it seems you extracted the sources as root and now you're trying to compile it as user (or you edited the Makefile inside the 'po' directory as root). You should do the whole process as user, except the ***make install*** part (by the way, I'd suggest you to install checkinstall from the repos and running *sudo checkinstall -D* instead of "make install" to convert the program into a nice .deb package and install it)

---

### Post by Crunchy_Yak on 2008-03-15
It appears as though your command 'sudo checkinstall -D' worked better, although it is stuck at this point:

======================== Installation successful ==========================

Copying documentation directory...
./
./TODO
./AUTHORS
./ChangeLog
./NEWS
./README
./INSTALL
./COPYING
grep: /var/tmp/ciJfeNLUqCALLgZRUeWll/newfile: No such file or directory

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...


It won't get past installing the Debian package.

---

