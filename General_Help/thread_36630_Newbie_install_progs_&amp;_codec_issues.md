---
title: "Newbie install progs &amp; codec issues"
date: 2005-05-24
forum: General Help
---

### Post by andrewsawyer on 2005-05-24
Hiya,

I hope someone can help shed some light on a number of issues I'm having.

1: I'm not sure where things are getting installed to.  For instance, I have installed "Three-dimensional" desktop switcher and AirCrack from the Synaptic Package Manager, and they are showing as being installed, however I can't find either in the program menus (or by clicking Applications >> Run Applications...).  Can anyone help me find them?

2: I would like to update FireFox to 1.04, and I have downloaded it from the website, but where do I install it to?  I have come from XP, and there is no 'Program Files' dir in Linux, so do I create one or something similar in my home directory, or do I install progs like this somewhere else?

3: I have tried to compile some programs (gDesklets being one) and I have run ./configure, however I get the following error:

-------------------------------------

checking for pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0... Package gobject-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gobject-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'gobject-2.0', required by 'PyGObject', not found

configure: error: Library requirements (pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

-------------------------------------

I have included the full screen of what prints out at the bottom if this text (incase it helps).  Looking at it, it'd seem that I didn't have the correct things installed, however taking pyorbit-2 >= 2.0.1 as an example, typing pyorbit into Synaptic Package Manager (searching by name and discription) gives 3 results, all of which are showing as installed.

4: Finally, I can't get mp3's or divx to run.  I have mPlayer installed, however trying to run an avi file through this results in it crashing.  Running it through Totem gives the error 'There were no decoders found to handle the stream...'.  I get pretty much the same error when trying to play an mp3 through Music Player.  Having said this, I have the Win32Codecs installed through Synaptic Package Manager.

If anyone could help with any of these issues, I would appreciate it greatly.

As mentioned above - full text for question 3:

root@ubuntu:/home/andy/Downloads/gDesklets-0.35rc1 # ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
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
checking how to run the C++ preprocessor... gcc -E
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
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
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for more warnings... no
checking for a Python interpreter with version >= 2.3... python
checking for python... /usr/bin/python
checking for python version... 2.4
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.4/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
checking /usr/include/python2.4/Python.h usability... yes
checking /usr/include/python2.4/Python.h presence... yes
checking for /usr/include/python2.4/Python.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking for pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0... Package gobject-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gobject-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'gobject-2.0', required by 'PyGObject', not found

configure: error: Library requirements (pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
root@ubuntu:/home/andy/Downloads/gDesklets-0.35rc1 #

---

### Post by poofyhairguy on 2005-05-24
[QUOTE=andrewsawyer]
2: I would like to update FireFox to 1.04, and I have downloaded it from the website, but where do I install it to?  I have come from XP, and there is no 'Program Files' dir in Linux, so do I create one or something similar in my home directory, or do I install progs like this somewhere else?[/QUOTE]

Use the backport. Really. Its better.

[QUOTE=andrewsawyer]4: Finally, I can't get mp3's or divx to run.  I have mPlayer installed, however trying to run an avi file through this results in it crashing.  Running it through Totem gives the error 'There were no decoders found to handle the stream...'.  I get pretty much the same error when trying to play an mp3 through Music Player.  Having said this, I have the Win32Codecs installed through Synaptic Package Manager.[/QUOTE]

Try gxine

sudo apt-get install gxine

Its my fav.

---

### Post by agds on 2005-05-24
I can't help you with the compiling, but I've recently dealt with the other issues you mentioned.  Unfortunately I'm writing this reply in XP, so I don't everything right in front of me.  Hopefully this still winds up being helpful.

1.  When you select a package in Synaptic, you should be able to click a "Properties" button in the toolbar.  One of the tabs in the window that opens lists installed files.  Usually the executable is located somewhere like /usr/bin or /usr/sbin or perhaps /etc.  I can't remember the exact paths.

2.  I seem to remember installing the latest version of Firefox using Synaptic.  You'll probably have to [add repositories](http://www.ubuntulinux.org/wiki/AddingRepositoriesHowto) first.

4.  Those [restricted formats](http://www.ubuntulinux.org/wiki/RestrictedFormats) can be a pain.  It's too bad win32codecs doesn't cover all your bases.  You'll probably need additional codecs and/or browser plug-ins.  That link offers fairly detailed instructions for the various formats you may want to play.

---

### Post by agds on 2005-05-24
[QUOTE=poofyhairguy]Try gxine

sudo apt-get install gxine

Its my fav.[/QUOTE]

I would also recommend totem-xine, if you're fond of the Totem interface.

---

### Post by andrewsawyer on 2005-05-24
Thanks guys.

Not at my PC at the mo, but I'll have another play tonight and see what it looks like following the suggestions given.

I'll post the outcome.  Fingers crossed that *might* be questions 1,2 and 4 answered.

**Anyone any ideas on Q3 - compiling issue?**

Thanks again,

Andy

---

### Post by agds on 2005-05-24
[QUOTE=andrewsawyer]
**Anyone any ideas on Q3 - compiling issue?**[/QUOTE]
It seems you're not the only one who has encountered problems with gobject-2.0 while compiling.  A quick Google search yielded some possibly relevant hits.  I didn't have time to look into each one, but perhaps you'll find something there.  Personally I would start by trying to locate gobject-2.0.pc so at least you'll know if it's there or not.  If it isn't, it could just be a matter of obtaining the package and putting it at the proper path.  Maybe someone else has more definitive advice...?

---

### Post by spikes2020 on 2006-01-05
hey i am also having problem installing stuff, every time i try sudo apt-get it cant seem to find it


spikes@Nerv5:~$ sudo apt-get install gxine
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gxine

so i just downloaded the files and un extracted them in the Home dir and did 

./configure
make

is that all i have to do for aircrack? and if so how do i run it, i read the readme and it did not mention much about it, if this question has been answerd before just post the link..


thanx

spikes2020

---

