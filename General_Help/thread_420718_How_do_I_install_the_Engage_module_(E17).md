---
title: "How do I install the Engage module? (E17)"
date: 2007-04-23
forum: General Help
---

### Post by raul_ on 2007-04-23
I really like the screenshots and I want to try it, but i can't find anything explaining how to do it.

---

### Post by worldwithoutgurus on 2007-04-23
Engage is dead. Go for Itask: it works for me.

Have a look here:
[http://marc.info/?l=enlightenment-devel&m=117725027908189&w=2](http://marc.info/?l=enlightenment-devel&m=117725027908189&w=2)

First of all, you need to install subversion.

And:
svn co [http://itask-module.googlecode.com/svn/trunk/](http://itask-module.googlecode.com/svn/trunk/) itask-module/itask_ng

Then:
cd ~/itask-module/itask_ng/itask_ng
./autogen.sh
make 
make install

Screenshot:
[http://perso.orange.fr/pinguSODalon/screens/itask.png](http://perso.orange.fr/pinguSODalon/screens/itask.png)

---

### Post by raul_ on 2007-04-23
Seems nice, but I get a "couldn't resolve hostname" error. I'll give it a try tomorrow. Thanks again :) What about elucence?

---

### Post by invaderjohn on 2007-06-03
> **worldwithoutgurus said:**
> Engage is dead. Go for Itask: it works for me.

Have a look here:
[http://marc.info/?l=enlightenment-devel&m=117725027908189&w=2](http://marc.info/?l=enlightenment-devel&m=117725027908189&w=2)

First of all, you need to install subversion.

And:
svn co [http://itask-module.googlecode.com/svn/trunk/](http://itask-module.googlecode.com/svn/trunk/) itask-module/itask_ng

Then:
cd ~/itask-module/itask_ng/itask_ng
./autogen.sh
make 
make install

Screenshot:
[http://perso.orange.fr/pinguSODalon/screens/itask.png](http://perso.orange.fr/pinguSODalon/screens/itask.png)


i rly cant get that to work
after i get the svn files i get the folders
~/itask-module/itask_ng/ <-- here i get both itask folder and ng folder
thou i want the ng version so i choose to cd to the ng folder,  the i run
./autogen.sh
and it starts
then make
then sudo make install
and i get the itask in my module lista but cant enable it.
i think that all of the files doesnt go into that ng folder like it should?


here's how it looks

./autogen.sh

Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
Generating gettext ng.pot.template
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
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
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for edje-config... /opt/e17/bin/edje-config
checking for enlightenment-config... /usr/bin/enlightenment-config
checking for efreet-config... /opt/e17/bin/efreet-config
configure: creating ./config.status
config.status: creating Makefile
config.status: creating data/Makefile
config.status: creating data/themes/Makefile
config.status: creating po/Makefile
config.status: creating src/Makefile
config.status: creating module.desktop
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing po-directories commands
config.status: executing default commands
john@ubuntu:~/itask-module/ng$ make
cd . && /bin/bash /home/john/itask-module/ng/missing --run autoheader
rm -f stamp-h1
touch config.h.in
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-recursive
make[1]: Entering directory `/home/john/itask-module/ng'
Making all in src
make[2]: Entering directory `/home/john/itask-module/ng/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/john/itask-module/ng/src'
Making all in data
make[2]: Entering directory `/home/john/itask-module/ng/data'
Making all in themes
make[3]: Entering directory `/home/john/itask-module/ng/data/themes'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/john/itask-module/ng/data/themes'
make[3]: Entering directory `/home/john/itask-module/ng/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/john/itask-module/ng/data'
make[2]: Leaving directory `/home/john/itask-module/ng/data'
Making all in po
make[2]: Entering directory `/home/john/itask-module/ng/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/john/itask-module/ng/po'
make[2]: Entering directory `/home/john/itask-module/ng'
make[2]: Leaving directory `/home/john/itask-module/ng'
make[1]: Leaving directory `/home/john/itask-module/ng'
john@ubuntu:~/itask-module/ng$ sudo make install
Password:
Making install in src
make[1]: Entering directory `/home/john/itask-module/ng/src'
make[2]: Entering directory `/home/john/itask-module/ng/src'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/home/john/.e/e/modules/ng/linux-gnu-i686" || mkdir -p -- "/home/john/.e/e/modules/ng/linux-gnu-i686"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'module.la' '/home/john/.e/e/modules/ng/linux-gnu-i686/module.la'
/usr/bin/install -c .libs/module.so /home/john/.e/e/modules/ng/linux-gnu-i686/module.so
/usr/bin/install -c .libs/module.lai /home/john/.e/e/modules/ng/linux-gnu-i686/module.la
/usr/bin/install -c .libs/module.a /home/john/.e/e/modules/ng/linux-gnu-i686/module.a
chmod 644 /home/john/.e/e/modules/ng/linux-gnu-i686/module.a
ranlib /home/john/.e/e/modules/ng/linux-gnu-i686/module.a
PATH="$PATH:/sbin" ldconfig -n /home/john/.e/e/modules/ng/linux-gnu-i686
----------------------------------------------------------------------
Libraries have been installed in:
   /home/john/.e/e/modules/ng/linux-gnu-i686

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
more information, such as the ld(1) and ld.so(Cool manual pages.
----------------------------------------------------------------------
make[2]: Leaving directory `/home/john/itask-module/ng/src'
make[1]: Leaving directory `/home/john/itask-module/ng/src'
Making install in data
make[1]: Entering directory `/home/john/itask-module/ng/data'
Making install in themes
make[2]: Entering directory `/home/john/itask-module/ng/data/themes'
make[3]: Entering directory `/home/john/itask-module/ng/data/themes'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/home/john/.e/e/modules/ng" || mkdir -p -- "/home/john/.e/e/modules/ng"
 /usr/bin/install -c -m 644 'fonts/VeraBd.ttf' '/home/john/.e/e/modules/ng/VeraBd.ttf'
 /usr/bin/install -c -m 644 'ng.edc' '/home/john/.e/e/modules/ng/ng.edc'
 /usr/bin/install -c -m 644 'ng.edj' '/home/john/.e/e/modules/ng/ng.edj'
make[3]: Leaving directory `/home/john/itask-module/ng/data/themes'
make[2]: Leaving directory `/home/john/itask-module/ng/data/themes'
make[2]: Entering directory `/home/john/itask-module/ng/data'
make[3]: Entering directory `/home/john/itask-module/ng/data'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/john/itask-module/ng/data'
make[2]: Leaving directory `/home/john/itask-module/ng/data'
make[1]: Leaving directory `/home/john/itask-module/ng/data'
Making install in po
make[1]: Entering directory `/home/john/itask-module/ng/po'
make[2]: Entering directory `/home/john/itask-module/ng/po'
make[2]: Nothing to be done for `install-exec-am'.
for L in it sv; do \
                /home/john/itask-module/ng/install-sh -d /home/john/.e/e/locale/$L/LC_MESSAGES; \
                /usr/bin/install -c -m 644 \
                $L.mo /home/john/.e/e/locale/$L/LC_MESSAGES/ng.mo; \
                done
make[2]: Leaving directory `/home/john/itask-module/ng/po'
make[1]: Leaving directory `/home/john/itask-module/ng/po'
make[1]: Entering directory `/home/john/itask-module/ng'
make[2]: Entering directory `/home/john/itask-module/ng'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/home/john/.e/e/modules/ng" || mkdir -p -- "/home/john/.e/e/modules/ng"
 /usr/bin/install -c -m 644 'module_icon.png' '/home/john/.e/e/modules/ng/module_icon.png'
 /usr/bin/install -c -m 644 'module.desktop' '/home/john/.e/e/modules/ng/module.desktop'
 /usr/bin/install -c -m 644 'e-module-ng.edj' '/home/john/.e/e/modules/ng/e-module-ng.edj'
make[2]: Leaving directory `/home/john/itask-module/ng'
make[1]: Leaving directory `/home/john/itask-module/ng'

---

### Post by RvX on 2007-06-03
```
rvx@rvx-desktop:~$ svn co http://itask-module.googlecode.com/svn/trunk/ itask-module/itask_ng
svn: REPORT request failed on '/svn/!svn/vcc/default'
svn: REPORT of '/svn/!svn/vcc/default': 400 Bad Request (http://itask-module.googlecode.com)

```
I can't download it for long time. What's wrong?

---

### Post by worldwithoutgurus on 2007-06-03
There have been some changes to the source.
Actually there are two different forms of the same module. Try them both and see which one works better for you.

svn co [http://itask-module.googlecode.com/svn/trunk/](http://itask-module.googlecode.com/svn/trunk/) itask-module/itask_ng

Then:

 cd ~/itask-module/itask_ng/itask
./autogen.sh
make 
sudo make install

And:

cd ~/itask-module/itask_ng/ng
./autogen.sh
make 
sudo make install

Works for me.

---

### Post by invaderjohn on 2007-06-03
> **worldwithoutgurus said:**
> There have been some changes to the source.
Actually there are two different forms of the same module. Try them both and see which one works better for you.

svn co [http://itask-module.googlecode.com/svn/trunk/](http://itask-module.googlecode.com/svn/trunk/) itask-module/itask_ng

Then:

 cd ~/itask-module/itask_ng/itask
./autogen.sh
make 
sudo make install

And:

cd ~/itask-module/itask_ng/ng
./autogen.sh
make 
sudo make install

Works for me.


still doesnt work
seems like it doesnt compile right

this is what happens when i load the module

[http://pici.se/pictures/XCytAQGOC.png](http://pici.se/pictures/XCytAQGOC.png)

its not possible for u to rar the files for me? 
so i can put those in right folders?
or are the files to spread?

would rly like to be able to use this thing

---

### Post by worldwithoutgurus on 2007-06-03
If you use E17 CVS it should work fine for you.
Is your installation up-to-date ?

See:
[http://perso.orange.fr/pinguSODalon/screens/itask.png](http://perso.orange.fr/pinguSODalon/screens/itask.png)
[http://perso.orange.fr/pinguSODalon/screens/itask_ng.png](http://perso.orange.fr/pinguSODalon/screens/itask_ng.png)

If you installed E17 from the repos, try updating. 
These modules may soon be available in binary format.

Source and binary don't mix well, make sure to uninstall the cvs version of itask modules first:
cd ~/itask-module/itask_ng/itask (ng)
sudo make uninstall
make clean
make distclean

---

### Post by invaderjohn on 2007-06-04
> **worldwithoutgurus said:**
> If you use E17 CVS it should work fine for you.
Is your installation up-to-date ?

See:
[http://perso.orange.fr/pinguSODalon/screens/itask.png](http://perso.orange.fr/pinguSODalon/screens/itask.png)
[http://perso.orange.fr/pinguSODalon/screens/itask_ng.png](http://perso.orange.fr/pinguSODalon/screens/itask_ng.png)

If you installed E17 from the repos, try updating. 
These modules may soon be available in binary format.

Source and binary don't mix well, make sure to uninstall the cvs version of itask modules first:
cd ~/itask-module/itask_ng/itask (ng)
sudo make uninstall
make clean
make distclean

im using the 0.16.999.038+cvs20070527-1 version if that ses anything :D
well well then i probobly have to w8 till its on the repros then?
or should i just go on trying. 
its just weird it ses the module.so doesnt exist cuz when i took a look in the folder the file was there

well well hope it gets out on the repro soon enough then.
cuz i have tried to reinstall this from svn like 10 times now n cant get it to work :/

EDIT: okej got it to work, had to change names of some folders fo ir to find it.
but now when i start it i get this big black border aruond like this
[[img]http://pici.se/thumbs/t_bkAdLGgEy.gif[/img]](http://pici.se/69433)

how do i change or remove that?. :O

---

### Post by worldwithoutgurus on 2007-06-04
Congratulations !

About the 'big black border'. The README says it all: 

'You need to have composite manager running like for example 
kompmgr(kdebase) xcompmgr or bling'

---

### Post by killaray on 2007-06-05
tryin to install this here, when i run ./autogen.sh i get the current error

```
Running aclocal...
aclocal: configure.in: 19: macro `AM_ENABLE_SHARED' not found in library
aclocal: configure.in: 20: macro `AM_PROG_LIBTOOL' not found in library
aclocal: macro `AM_PROG_MKDIR_P' required but not defined
aclocal: macro `AM_PROG_MKDIR_P' required but not defined

```

any ideas?

---

### Post by worldwithoutgurus on 2007-06-05
Make sure the gettext and libtool packages are installed on your system.

---

### Post by killaray on 2007-06-06
checked it out... libtools wasnt installed... installed and the first 2 errors went away but the last 2 remain

```
Running aclocal...
aclocal: macro `AM_PROG_MKDIR_P' required but not defined
aclocal: macro `AM_PROG_MKDIR_P' required but not defined
```

what could it be now?

---

### Post by worldwithoutgurus on 2007-06-06
Is m4 installed on your system ?
What version of automake are you using ?

---

### Post by RvX on 2007-06-06
> **invaderjohn said:**
> im using the 0.16.999.038+cvs20070527-1 version if that ses anything :D
well well then i probobly have to w8 till its on the repros then?
or should i just go on trying. 
its just weird it ses the module.so doesnt exist cuz when i took a look in the folder the file was there

well well hope it gets out on the repro soon enough then.
cuz i have tried to reinstall this from svn like 10 times now n cant get it to work :/

EDIT: okej got it to work, had to change names of some folders fo ir to find it.
but now when i start it i get this big black border aruond like this
[[img]http://pici.se/thumbs/t_bkAdLGgEy.gif[/img]](http://pici.se/69433)

how do i change or remove that?. :O

Hey, what directories you renamed?

---

### Post by killaray on 2007-06-06
> **worldwithoutgurus said:**
> Is m4 installed on your system ?
What version of automake are you using ?

i do have m4 installed... but when i type automake in terminal to check version it says i need something

```
automake: `configure.ac' or `configure.in' is required
```

i searched the forums and didnt find anything on those files

---

### Post by killaray on 2007-06-06
ok i fixed my issue... i went to this [thread](http://ubuntuforums.org/showthread.php?t=97199&highlight=itask) and installed all the required packages for E17 and then i ran autogen.sh and everything went fine.. ive installed everything A-ok

thanx for the help guys

---

### Post by killaray on 2007-06-06
> **RvX said:**
> Hey, what directories you renamed?

sudo nautilus and then head into .e/e/modules/itask/

there will be a folder in there named linux-gnu-i686 replace 686 to 486 then do the same thing in the ng folder

---

### Post by killaray on 2007-06-06
only issue i have no is where the hell can i find modules for this thing.. i need the bling module so that the black bar will disappear

---

### Post by killaray on 2007-06-06
ok searching on google i found out how to get modules from their CVS

[http://wiki.enlightenment.org/index.php/Gadgets](http://wiki.enlightenment.org/index.php/Gadgets)

check out their wiki its helpful

---

### Post by RvX on 2007-06-07
1. I have problem with bling. When I activated it, the screen became gray and there was nothing else. Any solutions?
2. I have iTask module installed, and the mess with it is weird. Sometimes when I click over the entry in taskbar, it raises proper window, but sometimes I click on entry and nothing happens - I have to use Alt+Tab to get into that window.

---

### Post by killaray on 2007-06-07
the grey problem is probably with the video driver ur using... and the itask module idk about really... i got it installed yesterday but the bling module deathly slowed everything down so i kinda quit on the enlightenment a bit... ill check it out when i get home and let u know everything seemed to be working fine though when i tried it...

also in regards to a dock if ur on gnome and want one i found a nice program called [AWN](http://awn.wetpaint.com/?t=anon).. it works similar to the dock on macs... pretty cool u should check it out

---

