---
title: "Kfreeflight onstall in Edgy"
date: 2007-03-07
forum: General Help
---

### Post by lakedad on 2007-03-07
I just came across the KfreeFlight package and would like to use it with the FlightGear simulator that I have running in Obuntu Edgy.....I have downloaded the KfreeFlight tarball and have it extracted on my desktop.....but can not get the software to install.....has anybody been able to install KfreeFlight in Edgy??   Any help/info would be appreciated 

thanks

---

### Post by Redeyes_Gambit on 2007-03-07
Have you installed the build-essentials package with synaptic?

```

sudo apt-get install build-essential

```

Have you ever built from source before? Oh, and did you get the develpment version or the stable?

---

### Post by lakedad on 2007-03-07
Yes I do have build-essentials installed....

No I have not built from source before....I am very new to Linux and Ubuntu.

I did get the stable version of Kfreeflight....

I have run ./configure  then make and have seen the compile almost complete...but at the end of the process I am getting the indication of an error noting that "X" can not be found and I needed to check the path in my install.....haven't got the foggiest idea of what that means other than the compile failed as a file could not be found.

I will admit I do not know what I am doing but I believe I have followed the install instructions provided by KfreeFlight.....

I guess my real question is whether anybody else has ever got KfreeFlight running with Ubuntu Edgy.....then of course it would be of great help to find out how it is done......Kfreeflight looks like a real assest to FlightGear.....would be nice if it showed up as a package for Ubuntu as the original FlightGear package did.

---

### Post by Redeyes_Gambit on 2007-03-08
Hm, sounds like you have a dependency unsatisfied. How EXACTLY does the .configure output read? Could you run it again and copy the errors here?

---

### Post by lakedad on 2007-03-08
Hi...


Here is a copy of the Terminal window showing the sequence that ended in the error indication....


doc@flightsimpc:~/Desktop/kfreeflight-0.2.1$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
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
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wno-non-virtual-dtor... yes
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
checking for egrep... grep -E
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
checking for PIE support... yes
checking if enabling -pie/fpie support... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
doc@flightsimpc:~/Desktop/kfreeflight-0.2.1$ 

Hope this points to the problem.....it looks like I am missing the "X includes".....I do not have a clue to what that means....but I did notice there was anothe post that indicated the same kind of missing "includes"......but I do not see that the problem was resolved.

Am I to believe others have got Kfreeflight to run with FlightGear in Ubuntu.....sure hope it will work together....that would b nice.

Thanks for your help....it is appreciated.

Regards

---

### Post by Redeyes_Gambit on 2007-03-08
Hopefully yes, it should be possible. It's all about how much effort needs to be put into it ;) .

Do you have the libx11-dev package installed?

```

sudo apt-get install libx11-dev

```

Edit:

Oh, it might also be Xorg dev file related. also try:

```

sudo apt-get install xorg-dev

```

and:

```

sudo apt-get install xserver-xorg-dev

```

---

### Post by lakedad on 2007-03-09
Thanks for your reply.....
It seems I did not have two of the three 'dev' packages you indicated.....

I loaded the first 'dev' package you referenced and tried to compile again....got the same error as before....

I loaded the second 'dev' package you referenced and again tried to compile.....this time I did get a different error....indicated I was missing a "Qt" file....here is a copy of the terminal info showing that error...

oc@flightsimpc:~/Desktop/kfreeflight-0.2.1$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
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
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wno-non-virtual-dtor... yes
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
checking for egrep... grep -E
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
checking for PIE support... yes
checking if enabling -pie/fpie support... yes
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
checking for libpng... no
checking for libjpeg6b... no
checking for libjpeg... no
configure: WARNING: libjpeg not found. disable JPEG support.
checking for perl... /usr/bin/perl
checking for Qt... configure: error: Qt (>= Qt 3.2 and < 4.0) (headers and libraries) not found. Please check your installation!


I also loaded the third 'dev' package you referenced and gt the indcation the info was already installed....

I have emailed the developer of Kfreeflight and he has responded by asking the following question....
tell me where your X include files and X libraries are----I will modify code.

Not sure I knw where/how t get the info he requested but it sounds like something has to be modified to run in Ubuntu.

He also asked if I had run the CVS package for KfreeFlight....I have not as I was not sure a CVS package would run in Ubuntu.

Hope this information helps isolating the problem in compiling.....I guess you are right when you say....the solution depends on how much you want t put into it.....dont mind the digging but i do need a lot of help as I know little about Linux itself.

Again many thanks for your assistance.....

regards

---

### Post by Redeyes_Gambit on 2007-03-09
Ahh, dependencies. Just be thankful that the dependencies so far have been in Synaptic :) . It gets really fun when you wind up having to compile your dependencies, which in turn have dependencies, which have dependencies etc etc etc lol. That's called dependency hell.

Well it looks like the X headers situation has been taken care of. No need bothering the developer with that situation any more. Now we have a QT dependency we have to look after. I think:

```

sudo apt-get install libqt3-headers

```

and/or

```

sudo apt-get install qt3-dev-tools

```

Should do the trick. Basically any time you get one of these errors you can fire up the Synaptic Package Manager and do a search for whatever it said it couldn't find. Chances are you will get a bazillion results. Out of the results if you look for titles that match closely (for instance, libqt3-headers or qt3-dev-tools and not qt-python-whatsamahoosit) and the words "dev", for development, or "lib", for library, then you will most likely resolve the dependency.

Lol, basically that's what I do when I'm trying to resolve any dependency that I encounter when compiling. I remember when I first started out with Ubuntu. Before I discovered Synaptic Package Manger I really missed the way Windows worked the .exe . Once I found out about Synaptic and .deb files things got a lot easier. 

Today it is even easier than when *I* started because .deb files can be double-clicked and the dependencies auto-magically get resolved. You used to have to resolve them by hand, just like compiling. I have a copy of Vista (got it for free through my school) but hardly use it because of how much I love the way Ubuntu works. Stick with it and soon enough you'll be an old pro.

---

### Post by lakedad on 2007-03-09
Hi....me again....
Installed the two items you referenced and they both installed OK....so must have needed them both too....tried a compile thereafter and got the "QT" error at the end again but it said something a little different.....here is a copy of the last couple of lines from the terminal

checking for Qt... configure: error: Qt (>= Qt 3.2 and < 4.0) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support


I also opened the config.log file and did a search on 'QT' to see if there was anything obvious to me........
looks like two files/directories are still missing....
  qconfig.h: No such file or directory
  qmodules.h: No such file or directory



I have copied a portion of the config.log and am sending it for your info.....the config.log file itself is too big too send.


configure:29752: checking for Qt
configure: 29817: /usr/lib/qt3/include/qstyle.h
configure: 29817: /usr/lib/qt3/qstyle.h
configure: 29817: /usr/lib/qt/include/qstyle.h
configure: 29817: /usr/lib/qt/qstyle.h
configure: 29817: /usr/share/qt3/include/qstyle.h
configure: 29817: /usr/share/qt3/qstyle.h
configure: 29817: /usr/local/qt/include/qstyle.h
configure: 29817: /usr/include/qt/qstyle.h
configure: 29817: /usr/include/qstyle.h
configure: 29817: /usr/X11R6/include/X11/qt/qstyle.h
configure: 29817: /usr/X11R6/include/qt/qstyle.h
configure: 29817: /usr/X11R6/include/qt2/qstyle.h
configure: 29817: /usr/include/qt3/qstyle.h
taking that
tried NO
tried /usr/lib/qt3/lib
tried /usr/lib/qt3
tried /usr/lib/qt/lib
tried /usr/lib/qt
configure:29935: rm -rf SunWS_cache; g++ -o conftest -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -I/usr/include/qt3 -I.  -DQT_THREAD_SUPPORT  -D_REENTRANT  -L/usr/share/qt3/lib -L/usr/lib     conftest.cc  -lqt-mt   -ldl  -lXext -lX11 -lSM -lICE  -lpthread 1>&5
In file included from conftest.cc:2:
/usr/include/qt3/qglobal.h:773:21: error: qconfig.h: No such file or directory
/usr/include/qt3/qglobal.h:783:22: error: qmodules.h: No such file or directory
configure:29938: $? = 1
configure: failed program was:
#include "confdefs.h"
#include <qglobal.h>
#include <qapplication.h>
#include <qcursor.h>
#include <qstylefactory.h>
#include <private/qucomextra_p.h>
#if ! (QT_VERSION >= 0x030200 && QT_VERSION < 0x040000)
#error 1
#endif

int main() {
    (void)QStyleFactory::create(QString::null);
    QCursor c(Qt::WhatsThisCursor);
    return 0;
}
configure:29978: error: Qt (>= Qt 3.2 and < 4.0) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support!


Obviously there is much more to learn about Ubuntu....but from what I have seen over the few weeks i have been running it, it will be worth the trouble....it is quite different than anything else I have worked with.....and i go all the way back to analog computers.....and still have my TRS-80 and loved DOS.....   :)

Let me know what you see in the 'tea leaves' I have sent....and thanks again.

Regards
Doc
Lake Gaston  NC   (home of tall pines and big mouth bass)

---

### Post by Redeyes_Gambit on 2007-03-09
Ahh, apparently it wants QT with multi-thread support (hence the MT) 

*drops into computer-guru meditation state*

...Hmmm, Tea-leaves no good... Me try coffee grounds...

```

sudo apt-get install libqt3-mt

```

and/or

```

sudo apt-get install libqt3-mt-dev

```

Ahh NC ay? I used to live in Greenville SC and still have relatives in Ashville NC. Beautiful place.

---

### Post by lakedad on 2007-03-09
Wow....:shock:    almost there....I think!   :)

Installing libqt3-mt indicated that I already had that version but installing libqt3-mt-dev did install....so that was needed.....when I ran the compile I "almost" completed but did get another error....here is a copy of the ending.

checking for rpath... yes
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!


Is this the area that the developer might have needed to change his code??

Hopefully you are getting me closer to the finish line....dont think I can 'sprint' to the finish but plodding along is still progress.

How long have you been involved with the 'gizzards' of Ubuntu and Linux??  Are you a programmer by nature or a hobbyist.....I cant claim to be either....just a hacker I guess.

Lake Gaston is in the center of the state and borders the NC/VA stateline....a very rural area and a great place to live.

You have given me a lot of your time and good advise.....again want to thank you for your help.

Regards
Doc

---

### Post by Redeyes_Gambit on 2007-03-09
Lol, I've plodded all my life. Sprinting just makes for more painful falls :D .

As for how long I've been involved in Linux/Ubuntu; not that long really. I've been a "hacker" (in the classical 1960/70's sense of the word) for most of the past several years. I also taught myself to repair computers, with the help of several key individuals. Eventually I expended all the cool and free software available for Windows and decided to go Linux. 

Started out with Knoppix to get the feel of Linux, diverged down the Meppis path for a while but was repelled by their lack of support. Tried Debian but wound up having install issues... Finally a good friend of mine who got me started in computer repair pointed me in the direction of Ubuntu. I got in on the whole Ubuntu bandwagon at version 5.10 if I'm not mistaken. Started out dual-booting between Ubuntu and Win 98se, moved up to XP and kept Ubuntu, then moved up to Vista and STILL kept Ubuntu. Today Ubuntu is my primary OS and the only time I go back to using Windows is for games and school (I'm in computer-related college classes or I would do school in Ubuntu too.)

Ok, enough of my personal history and on to the fixin'. :)

It's a tad harder to track down KDE based dependencies since KDE is absolutely huge... BUT I think one of these ought to get us over the last hurdle:

```

sudo apt-get install kdebase-dev

```

```

sudo apt-get install kde-devel

```

Lol, the second one is actually a meta-package (one package that "pulls in" a whole bunch of other packages) and probably had all the QT stuff we needed earlier. 20/20 hindsight.

---

### Post by lakedad on 2007-03-09
good news.... :)   it did compile

bad news.... :(   dont know what happened to the program

After installing the Kde dev items i ran a compile and it showed it completed successfully and stated I could perform a "make".....I entered Make and got an error indicating there was no such file or directory.....now I can find the files/program that compiled.

I thought the compiled program would show up in /user/games....but nothing is there....

There must be a secret entry yet to be made.....do I see a finish line ahead??

So close...... :confused: 

Guess I will wrap it up for tonight.....will try some more tomorrow.....

Goodnight
Doc

---

### Post by Redeyes_Gambit on 2007-03-10
Hmm.. Well it sounds like we finally resolved all the dependencies. Now, did you type in "Make" or "make"?

Unlike DOS, Linux has a case-sensitive command line. Don't capitalize where you should, or capitalize where you shouldn't and things usually don't wind up working :) .

One thing of note: I'm guessing the instructions want you to type "make install" at some point yes? Something that I have figured out is that you almost never want to use "make install." There is a great little program called "checkinstall" that provides the same functionality as make install, but allows you to remove whatever program you compiled through Synaptic, instead of having to rely on whatever un-install the programmer may or may not have included. Thus it generally provides cleaner un-installs.

First we have to get checkinstall:

```

sudo apt-get install checkinstall

```

Now, ANY time you see instructions tell you to issue the command "make install" substitute:

```

checkinstall

```

after you issue "checkinstall" you will get walked through a little text menu where you fill in information about the program. Basically this is for your good alone so don't worry if you cant fill in a field with a proper value. For instance, it will ask about what version you compiled. Sometimes I don't know so I just enter any old number. Again, it won't matter because the information is just there for your benefit when you are looking through Synaptic. Just make sure the "title" (or maybe it was "name") field is something you will remember so if you need to un-install the program later you can just type in a search in Synaptic and find the package to un-install. :)

---

### Post by lakedad on 2007-03-10
Hi...me again...just finished some yard work and turned on the PC and found your reply.

Tried the 'checkinstall' procedure.....everything ran as you described but the install aborted as it appears I am missing a couple of files....aclocal-1.9 and automake-1.9.....again dont know what they are  :confused:

Here is a copy of the CheckInstall Results

========================= Installation results ===========================
cd . && make -f admin/Makefile.common configure.in ;
make[1]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1'
*** Creating configure.files
make[1]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1'
cd . && /bin/bash /home/doc/Desktop/kfreeflight-0.2.1/admin/missing --run aclocal-1.9 
/home/doc/Desktop/kfreeflight-0.2.1/admin/missing: line 52: aclocal-1.9: command not found
WARNING: `aclocal-1.9' is missing on your system.  You should only need it if
         you modified `acinclude.m4' or `configure.in'.  You might want
         to install the `Automake' and `Perl' packages.  Grab them from
         any GNU archive site.
 cd . && /bin/bash /home/doc/Desktop/kfreeflight-0.2.1/admin/missing --run automake-1.9 --gnu 
/home/doc/Desktop/kfreeflight-0.2.1/admin/missing: line 52: automake-1.9: command not found
WARNING: `automake-1.9' is missing on your system.  You should only need it if
         you modified `Makefile.am', `acinclude.m4' or `configure.in'.
         You might want to install the `Automake' and `Perl' packages.
         Grab them from any GNU archive site.
 cd . && perl admin/am_edit 
/bin/pwd: couldn't find directory entry in `../../../../..' with matching i-node
/bin/pwd: couldn't find directory entry in `../../../../..' with matching i-node
Use of chdir('') or chdir(undef) as chdir() is deprecated at /usr/share/perl/5.8/File/Find.pm line 802.
cd . && perl admin/am_edit Makefile.in
/bin/pwd: couldn't find directory entry in `../../../../..' with matching i-node
/bin/pwd: couldn't find directory entry in `../../../../..' with matching i-node
cd . && rm -f configure
cd . && make -f admin/Makefile.common configure
make[1]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1'
Can't open configure: No such file or directory.
make[1]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1'
/bin/bash ./config.status --recheck
running /bin/bash ./configure   --no-create --no-recursion
/bin/bash: ./configure: No such file or directory
make: *** [config.status] Error 127

****  Installation failed. Aborting package creation.

By the way in answer to your question about what did I enter....make or Make....
I think I entered 'make'.....I also did try 'install make'....same result as 'make'.....but thanks for reminding me about the case sensitive thing....i think I knew that...but will make sure I remember that....and did not know about the catch to using "make".

Again thanks for your time....you need to consider writing a book....like Ubuntu for Dummies......have to believe it would be a best seller.   :)  

Where do we go from here??

Regards
Doc

---

### Post by Redeyes_Gambit on 2007-03-10
Ahh, well automake1.9 is an easy one.

```

sudo apt-get install automake1.9

```

I'm hoping that will also resolve the aclocal problem. If not then we will need to try a few python dependencies.

Lol, as for the book I'm afraid I could only be a co-author at best ;) . I have my own issues that I ask about here and wind up learning a lot. My latest project is getting a driver to compile for a SATAII RAID card. Ungh. It's killing me. I owe a great deal of what I know to other people on this most excellent of forums. Everybody give yourselves a pat on the back! :D

Oh, and usually you do a "make install" (or in our case checkinstall) ONLY AFTER a successful "make." Two separate commands. Lol I suppose I should have made that more clear. Sorry for any confusion :) .

Just FYI, On the site the instructions combine the ".configure" step and the "make" step by using "&&" . Like thus:

```

./configure && make

```

"&&" can be used to execute a series of commands (if I am not mistaken) by typing one command, then "&&", then the next command. So, normally one issues .configure, waits for it to finish, then executes "make", then "make install" or "checkinstall". 

.configure (gasp) configures the program you're trying to compile, but does not actually compile it. "make" does the compiling if I'm not terribly confused, then "make install" or "checkinstall" actually does the installing.

Ok, that's our edu-k-shun-l lesson for the day ;) .

---

### Post by lakedad on 2007-03-10
Installed the 'automake1.9' file and tried a new install....may have a tougher error now....something about an 'undefined macro'....that doesn't sound good.:shock: 

Here is a copy of the installation results....

======================== Installation results ===========================
cd . && rm -f configure
cd . && make -f admin/Makefile.common configure
make[1]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1'
configure.in:43: error: possibly undefined macro: AM_INIT_AUTOMAKE
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:48: error: possibly undefined macro: AM_CONFIG_HEADER
configure.in:51: error: possibly undefined macro: AC_CHECK_COMPILERS
configure.in:52: error: possibly undefined macro: AC_ENABLE_SHARED
configure.in:53: error: possibly undefined macro: AC_ENABLE_STATIC
configure.in:58: error: possibly undefined macro: AM_KDE_WITH_NLS
configure.in:61: error: possibly undefined macro: AC_PATH_KDE
configure.in:70: error: possibly undefined macro: AC_CHECK_KDEMAXPATHLEN
make[1]: *** [configure] Error 1
make[1]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1'
make: *** [configure] Error 2

****  Installation failed. Aborting package creation.


Hope this is making sense to you...as i have not the faintest idea of what a 'token' is or what an 'M4-pattern-allow' should do :confused:  

Thanks for the lesson on configure.....will use the && entry....and the description of what config and make do is appreciated...makes sense now.....thanks

Hope your progress on the SATII Raid driver is coming along...cant imagine how to begin that effort....you got a good thing going....  :) 

Let me know what you think about the latest error.....by the way is there a limit on the number of compile/install error Ubuntu will tolerate....hope not!

Regards
Doc

---

### Post by Redeyes_Gambit on 2007-03-10
Hmm... This one is a bit of a puzzle.

Oh, and as for a limit on compiles, no there isn't a limit :) .

Let's try a clean compile. Probably not the answer but worth a shot:

```

cd /home/doc/Desktop/kfreeflight-0.2.1

```

I'm assuming that is where you have your source code. Since you have used DOS then I'm sure you're used to using "cd" :) . Now type:

```

sudo make clean

```

That will clean out all the partial compile/compile garbage. I'm not entirely sure when to clean, but I always run "make clean" before I get ready to compile something for the first time, or if I'm compiling a new version of something.

Then we will do the all too familiar:

```

sudo ./configure

```

Then let that run. Since we are here it's time for another lesson :) . Any time you need to execute a script (usually installs. Java for instance installs through a script) "./" is the command you use to execute the script. Most of the time you have to use it with "sudo" for super-user privileges. OK, next step:

```

sudo make

```

Then let that run. And finally, if we make (no pun intended) it that far:

```

sudo checkinstall

```

I'll be here when you're through :D .

---

### Post by lakedad on 2007-03-10
:shock:  good grief.....cant even do a clean uninstall.....getting an error trying that :confused: 

Here is a copy of the terminal events after I tried the 'make clean'.....

doc@flightsimpc:~/Desktop/kfreeflight-0.2.1$ sudo make clean
/bin/bash ./config.status --recheck
running /bin/bash ./configure   --no-create --no-recursion
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
./configure: line 1851: syntax error near unexpected token `kfreeflight,'
./configure: line 1851: `AM_INIT_AUTOMAKE(kfreeflight, 0.2.1)'
make: *** [config.status] Error 2


Is the 'AM-INIT AUTOMAKE' one of the missing files I had seen reported in the earleir install attempts??

I am at my PC now if you are still at yours....by the way are you ever away from your PC  :lolflag: 

regards
doc

---

### Post by Redeyes_Gambit on 2007-03-10
Lol, nope, not really. I'm either doing school or working on my own projects :) . OK, try this:

1. launch Synaptic. It's under System>Administration>Synaptic Package Manager. You will have to provide your password.

2. Hit "reload" to get the latest list of packages.

3. Do a search for "automake"

4. There should be only one green box "lit" by automake1.9 if any other version is "lit" right-click on it and hit "mark for complete removal." If a box pops up saying that other things need to be removed as well, cancel out and don't un-install that version of automake.

5. Since we are already in Synaptic we will look for the following packages there instead of using the usual "apt-get install." Click on search again and type "autoconf". If version 2.60-1 is not installed, then mark it by right-clicking on it and clicking "Mark for installation". Completely remove any older version unless Synaptic complains about having to remove something else.

6. One last search; This time for "libtool". Mark version 1.5.22-4 for installation.

7. Once you have finished marking what you want hit "Apply." It should be a big check mark button near the top. Your packages will download and install. Now try the "make clean" instructions above again :) .

---

### Post by lakedad on 2007-03-10
followed your last instructions for using Synaptic and the only thing I had to do (the first two file were OK) was install 'libtool 1.5.22-4....that installed OK...

but running the 'sudo make clean' ended with the same error as I got earlier...here's a copy..

doc@flightsimpc:~$ cd /home/doc/Desktop/kfreeflight-0.2.1
doc@flightsimpc:~/Desktop/kfreeflight-0.2.1$ sudo make clean
Password:
/bin/bash ./config.status --recheck
running /bin/bash ./configure   --no-create --no-recursion
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
./configure: line 1851: syntax error near unexpected token `kfreeflight,'
./configure: line 1851: `AM_INIT_AUTOMAKE(kfreeflight, 0.2.1)'
make: *** [config.status] Error 2
doc@flightsimpc:~/Desktop/kfreeflight-0.2.1$ 

since kfreeflight is designed by a French guy...maybe we need to edit the 'AM-INIT-AUTOMAKE' instruction to 'FR-INIT-AUTOMAKE'??    
:lol: Hey am I learning or not

regards
Doc  (aka grasshopper)

---

### Post by Redeyes_Gambit on 2007-03-10
LOL @ the FR-INIT-AUTOMAKE.

Hm. Most be-puzzling. Well I'm afraid it must wait for the 'morrow. Daylight Savings time starts either tonight or tomorrow and so though it's only 10:00 here, it will feel like I got to bed at 11:00.

Perhaps daylight will illuminate the problem. :)

Have a good'n!

---

### Post by lakedad on 2007-03-10
yes...same here....it's already tomorrow in daylight saving time......who was it that came up with this great idea.....now my digital watch wont work....cant find the instruction on which buttons to press.....nothing is simple anymore.....:confused: 

Hope to catch you tomorrow....

regards
doc

---

### Post by Redeyes_Gambit on 2007-03-11
Good mornin'! 

Ok, I have an idea. Since we are having some issues even with make clean we are going to try from scratch. Go ahead and delete the extracted version of kfreeflight. Re-extract a fresh copy from the archive (the .tar file) and do the usual:

```

sudo ./configure

```

```

sudo make

```

```

sudo checkinstall

```

---

### Post by lakedad on 2007-03-11
Hi...morning....think it is still morning in AZ....even with dayight saving....

deleted the original extracted file and made a new one.....recompiled and and aftr doing the 'cleaninstall' did see a much long run of the install but it too ended in an error...
Here's acopy of what happened.....hope the file is small enough to send....



Good - your configure finished. Start make now

doc@flightsimpc:~/Desktop/kfreeflight-0.2.1$ sudo checkinstall

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> kfreeflight
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@flightsimpc ]
1 -  Summary: [ kfreeflight ]
2 -  Name:    [ kfreeflight ]
3 -  Version: [ 0.2.1 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ kfreeflight-0.2.1 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
cd . && make -f admin/Makefile.common configure.in ;
make[1]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1'
*** Creating configure.files
make[1]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1'
cd . && /bin/bash /home/doc/Desktop/kfreeflight-0.2.1/admin/missing --run aclocal-1.9 
/usr/share/aclocal/libmcrypt.m4:17: warning: underquoted definition of AM_PATH_LIBMCRYPT
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
 cd . && /bin/bash /home/doc/Desktop/kfreeflight-0.2.1/admin/missing --run automake-1.9 --gnu 
 cd . && perl admin/am_edit 
/bin/pwd: couldn't find directory entry in `../../../../..' with matching i-node
/bin/pwd: couldn't find directory entry in `../../../../..' with matching i-node
Use of chdir('') or chdir(undef) as chdir() is deprecated at /usr/share/perl/5.8/File/Find.pm line 802.
cd . && perl admin/am_edit Makefile.in
/bin/pwd: couldn't find directory entry in `../../../../..' with matching i-node
/bin/pwd: couldn't find directory entry in `../../../../..' with matching i-node
cd . && rm -f configure
cd . && make -f admin/Makefile.common configure
make[1]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1'
make[1]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1'
/bin/bash ./config.status --recheck
running /bin/bash ./configure   --no-create --no-recursion
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
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
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wno-non-virtual-dtor... yes
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
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
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
checking for PIE support... yes
checking if enabling -pie/fpie support... yes
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
checking for xmllint... /usr/bin/xmllint
checking whether byte ordering is bigendian... no
checking for MAXPATHLEN... 4096
checking if admin should be compiled... no
checking if doc should be compiled... yes
checking if po should be compiled... yes
checking if src should be compiled... yes
configure: creating ./config.status
wrong input (flag != 4) at admin/conf.change.pl line 117, <> line 1221.

Good - your configure finished. Start make now

 /bin/bash ./config.status
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating doc/en/Makefile
config.status: creating po/Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: executing depfiles commands
Making install in doc
make[1]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1/doc'
make[2]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1/doc'
make[3]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1/doc'
make[2]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1/doc'
make[1]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1/doc'
Making install in po
make[1]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1/po'
make[2]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1/po'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1/po'
make[1]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1/po'
Making install in src
make[1]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.cpp; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
In file included from kfreeflight.h:47,
                 from main.cpp:24:
kfreeflight_view.h:69:24: error: mainwindow.h: No such file or directory
In file included from pref.h:45,
                 from kfreeflight.h:49,
                 from main.cpp:24:
fgpref.h:26:32: error: flightgearsettings.h: No such file or directory
In file included from pref.h:46,
                 from kfreeflight.h:49,
                 from main.cpp:24:
atlaspref.h:33:27: error: atlassettings.h: No such file or directory
kfreeflight_view.h:73: error: expected class-name before ‘{’ token
kfreeflight_view.h:77: error: ‘WFlags’ has not been declared
fgpref.h:33: error: expected class-name before ‘{’ token
fgpref.h:37: error: ‘WFlags’ has not been declared
atlaspref.h:36: error: expected class-name before ‘{’ token
atlaspref.h:40: error: ‘WFlags’ has not been declared
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.



is the end near??   If it does run I hope it is as nice as the 'manual' showed it to be.

regards
doc

---

### Post by Redeyes_Gambit on 2007-03-11
Ok, I'm having a little trouble understanding the order you did things in... it's silly to ask after you have done this half a dozen times but the logs look like you executed checkinstall before make (?) :D

Maybe it's just the order you put the logs up in your post? Lol, it makes things somewhat confusing :P

---

### Post by lakedad on 2007-03-11
I am reasonably sure that I made the entries in the right order...but can not say for sure now....I will start over with a new compile and get back to you shortly.....I think I am having another 'senior moment"......:) 

sorry...but remember I am still the grasshopper and you are the master....will try harder

Doc

---

### Post by Redeyes_Gambit on 2007-03-11
ROFL. 

If roo can snatch thees compile from my hand, then you too shall be a masta grashoppah!

---

### Post by lakedad on 2007-03-11
OK...started over and did a new compile with the extracted Kfreeflight file.....made sure i entered the sequence correctly.....the install failed again but the log does appear different than the first....dont know what that was about but in the latest copy of the terminal file I again see the comment   "Good your configure complete...start make now" but this time it doesn't show up until near the end of the install process....
Here is a copy of the latest Terminal file.....

doc@flightsimpc:~/Desktop/kfreeflight-0.2.1$ sudo checkinstall

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> kfreeflight  
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@flightsimpc ]
1 -  Summary: [ kfreeflight ]
2 -  Name:    [ kfreeflight ]
3 -  Version: [ 0.2.1 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ kfreeflight-0.2.1 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
cd . && make -f admin/Makefile.common configure.in ;
make[1]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1'
*** Creating configure.files
make[1]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1'
cd . && /bin/bash /home/doc/Desktop/kfreeflight-0.2.1/admin/missing --run aclocal-1.9 
/usr/share/aclocal/libmcrypt.m4:17: warning: underquoted definition of AM_PATH_LIBMCRYPT
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
 cd . && /bin/bash /home/doc/Desktop/kfreeflight-0.2.1/admin/missing --run automake-1.9 --gnu 
 cd . && perl admin/am_edit 
/bin/pwd: couldn't find directory entry in `../../../../..' with matching i-node
/bin/pwd: couldn't find directory entry in `../../../../..' with matching i-node
Use of chdir('') or chdir(undef) as chdir() is deprecated at /usr/share/perl/5.8/File/Find.pm line 802.
cd . && perl admin/am_edit Makefile.in
/bin/pwd: couldn't find directory entry in `../../../../..' with matching i-node
/bin/pwd: couldn't find directory entry in `../../../../..' with matching i-node
cd . && rm -f configure
cd . && make -f admin/Makefile.common configure
make[1]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1'
make[1]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1'
/bin/bash ./config.status --recheck
running /bin/bash ./configure   --no-create --no-recursion
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
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
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wno-non-virtual-dtor... yes
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
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
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
checking for PIE support... yes
checking if enabling -pie/fpie support... yes
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
checking for xmllint... /usr/bin/xmllint
checking whether byte ordering is bigendian... no
checking for MAXPATHLEN... 4096
checking if admin should be compiled... no
checking if doc should be compiled... yes
checking if po should be compiled... yes
checking if src should be compiled... yes
configure: creating ./config.status
wrong input (flag != 4) at admin/conf.change.pl line 117, <> line 1221.

Good - your configure finished. Start make now

 /bin/bash ./config.status
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating doc/en/Makefile
config.status: creating po/Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: executing depfiles commands
Making install in doc
make[1]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1/doc'
make[2]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1/doc'
make[3]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1/doc'
make[2]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1/doc'
make[1]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1/doc'
Making install in po
make[1]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1/po'
make[2]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1/po'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1/po'
make[1]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1/po'
Making install in src
make[1]: Entering directory `/home/doc/Desktop/kfreeflight-0.2.1/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.cpp; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
In file included from kfreeflight.h:47,
                 from main.cpp:24:
kfreeflight_view.h:69:24: error: mainwindow.h: No such file or directory
In file included from pref.h:45,
                 from kfreeflight.h:49,
                 from main.cpp:24:
fgpref.h:26:32: error: flightgearsettings.h: No such file or directory
In file included from pref.h:46,
                 from kfreeflight.h:49,
                 from main.cpp:24:
atlaspref.h:33:27: error: atlassettings.h: No such file or directory
kfreeflight_view.h:73: error: expected class-name before ‘{’ token
kfreeflight_view.h:77: error: ‘WFlags’ has not been declared
fgpref.h:33: error: expected class-name before ‘{’ token
fgpref.h:37: error: ‘WFlags’ has not been declared
atlaspref.h:36: error: expected class-name before ‘{’ token
atlaspref.h:40: error: ‘WFlags’ has not been declared
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/doc/Desktop/kfreeflight-0.2.1/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.



looks like 'WFlags" is a problem??   guess I am still the grasshopper  :( 

One comment related to the 'sudo make' entry when doing the compile.....I have always received an error when that entry is made....it states...'no targets specified and no makefile found'......I then entered'sudo./configure' again and the config process started OK....I read somewhere that was normal.....is that correct??  Should have mentioned this earlier but i thought it was "normal".

regards
doc

---

### Post by Redeyes_Gambit on 2007-03-11
Hm. It's kinda odd that make can't find the makefile off the bat. ./configure is what is supposed to create a makefile (I believe) so... I don't know what that means lol.

Well, this is turning into a nightmare. Normally we have a nice compiled product by now :D . Perhaps it would be easier to try the development version (never thought I'd say that!) Maybe it has these kinks worked out. (Yes, I am running out of ideas lol)

So, if you're up on trying the development version, go grab the source code off of sourceforge at: [http://downloads.sourceforge.net/kfreeflight/kfreeflight-0.3.2-r2.tar.gz?modtime=1145464607&big_mirror=0](http://downloads.sourceforge.net/kfreeflight/kfreeflight-0.3.2-r2.tar.gz?modtime=1145464607&big_mirror=0)

Then we will need a few more dependencies :rolleyes:

```

sudo apt-get install zlib1g

```

```

sudo apt-get install zlib1g-dev

```

```

sudo apt-get install kdetoys

```

```

sudo apt-get install libglut3

```

```

sudo apt-get install libglut3-dev 

```

```

sudo apt-get install freeglut3

```

```

sudo apt-get install freeglut3-dev

```

```

sudo apt-get install plib1.8.4c2

```

```

sudo apt-get install plib1.8.4-dev

```

```

sudo apt-get install simgear0

```

```

sudo apt-get install simgear-dev

```

Then cd into the unzipped kflight development version file directory and type:

```

sudo ./configure

```

```

sudo make clean

```


```

sudo make

```


```

sudo checkinstall

```

And if THAT, ALL OF THAT, doesn't work then I will be at something of my whit's end!

---

### Post by lakedad on 2007-03-11
:(    I think we are at whit's end....:confused: 
Got the dev version of kfreeflight and all of the dependancies you referenced  (wow where did you find that stuff).....installed everything Ok and compiled the dev version without any problem....other than when I did the 'sudo makeclean' entry I got the error "no rule to make target 'clean'....once again I reentered 'sudo ./configure' and th compile was initiated and successfully competed.

Then when I ran the 'sudo checkinstall' the process ran the same but also seemed to run longer but again ended in the abort just as with the original install process.....but there are a number of different 'error' statements that show a lot of missing "flightgear" stuff....seems like a lot of files are missing....

here's the terminal copy of the install process....


doc@flightsimpc:~/Desktop/kfreeflight-0.3.2$ sudo checkinstall

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> kfreeflight
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@flightsimpc ]
1 -  Summary: [ kfreeflight ]
2 -  Name:    [ kfreeflight ]
3 -  Version: [ 0.3.2 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ kfreeflight-0.3.2 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
cd . && make -f admin/Makefile.common configure.in ;
make[1]: Entering directory `/home/doc/Desktop/kfreeflight-0.3.2'
*** Creating configure.files
make[1]: Leaving directory `/home/doc/Desktop/kfreeflight-0.3.2'
cd . && /bin/bash /home/doc/Desktop/kfreeflight-0.3.2/admin/missing --run aclocal-1.9 
/usr/share/aclocal/libmcrypt.m4:17: warning: underquoted definition of AM_PATH_LIBMCRYPT
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
 cd . && /bin/bash /home/doc/Desktop/kfreeflight-0.3.2/admin/missing --run automake-1.9 --gnu 
 cd . && perl admin/am_edit 
/bin/pwd: couldn't find directory entry in `../../../../..' with matching i-node
/bin/pwd: couldn't find directory entry in `../../../../..' with matching i-node
Use of chdir('') or chdir(undef) as chdir() is deprecated at /usr/share/perl/5.8/File/Find.pm line 802.
cd . && perl admin/am_edit Makefile.in
/bin/pwd: couldn't find directory entry in `../../../../..' with matching i-node
/bin/pwd: couldn't find directory entry in `../../../../..' with matching i-node
cd . && rm -f configure
cd . && make -f admin/Makefile.common configure
make[1]: Entering directory `/home/doc/Desktop/kfreeflight-0.3.2'
make[1]: Leaving directory `/home/doc/Desktop/kfreeflight-0.3.2'
/bin/bash ./config.status --recheck
running /bin/bash ./configure   --no-create --no-recursion
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
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
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wno-non-virtual-dtor... yes
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
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
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
checking for PIE support... yes
checking if enabling -pie/fpie support... yes
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
checking for xmllint... /usr/bin/xmllint
checking whether byte ordering is bigendian... no
checking for MAXPATHLEN... 4096
checking for glAccum in -lGL... yes
checking for gluBeginCurve in -lGLU... yes
checking for glXChooseVisual in -lglut... yes
checking for glutInit in -lglut... yes
checking simgear/version.h usability... yes
checking simgear/version.h presence... yes
checking for simgear/version.h... yes
checking plib/ul.h usability... yes
checking plib/ul.h presence... yes
checking for plib/ul.h... yes
checking if admin should be compiled... no
checking if doc should be compiled... yes
checking if po should be compiled... yes
checking if src should be compiled... yes
configure: creating ./config.status
wrong input (flag != 4) at admin/conf.change.pl line 117, <> line 1234.


Good - your configure finished. Start make now

 /bin/bash ./config.status
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating doc/en/Makefile
config.status: creating po/Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: executing depfiles commands
Making install in doc
make[1]: Entering directory `/home/doc/Desktop/kfreeflight-0.3.2/doc'
make[2]: Entering directory `/home/doc/Desktop/kfreeflight-0.3.2/doc'
make[3]: Entering directory `/home/doc/Desktop/kfreeflight-0.3.2/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/doc/Desktop/kfreeflight-0.3.2/doc'
make[2]: Leaving directory `/home/doc/Desktop/kfreeflight-0.3.2/doc'
make[1]: Leaving directory `/home/doc/Desktop/kfreeflight-0.3.2/doc'
Making install in po
make[1]: Entering directory `/home/doc/Desktop/kfreeflight-0.3.2/po'
make[2]: Entering directory `/home/doc/Desktop/kfreeflight-0.3.2/po'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/doc/Desktop/kfreeflight-0.3.2/po'
make[1]: Leaving directory `/home/doc/Desktop/kfreeflight-0.3.2/po'
Making install in src
make[1]: Entering directory `/home/doc/Desktop/kfreeflight-0.3.2/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../src   -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.cpp; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
In file included from kfreeflight_window.h:49,
                 from kfreeflight.h:42,
                 from main.cpp:24:
kfreeflight_view.h:68:24: error: mainwindow.h: No such file or directory
In file included from kfreeflight_view.h:69,
                 from kfreeflight_window.h:49,
                 from kfreeflight.h:42,
                 from main.cpp:24:
weather_view.h:26:21: error: weather.h: No such file or directory
In file included from kfreeflight_view.h:70,
                 from kfreeflight_window.h:49,
                 from kfreeflight.h:42,
                 from main.cpp:24:
airport_view.h:42:21: error: airport.h: No such file or directory
In file included from airport_view.h:43,
                 from kfreeflight_view.h:70,
                 from kfreeflight_window.h:49,
                 from kfreeflight.h:42,
                 from main.cpp:24:
world_view.h:39:19: error: world.h: No such file or directory
In file included from airport_view.h:44,
                 from kfreeflight_view.h:70,
                 from kfreeflight_window.h:49,
                 from kfreeflight.h:42,
                 from main.cpp:24:
research_view.h:34:22: error: research.h: No such file or directory
In file included from pref.h:48,
                 from kfreeflight_window.h:50,
                 from kfreeflight.h:42,
                 from main.cpp:24:
fgpref.h:26:32: error: flightgearsettings.h: No such file or directory
In file included from pref.h:49,
                 from kfreeflight_window.h:50,
                 from kfreeflight.h:42,
                 from main.cpp:24:
fgprefbis.h:30:35: error: flightgearsettingsbis.h: No such file or directory
In file included from pref.h:50,
                 from kfreeflight_window.h:50,
                 from kfreeflight.h:42,
                 from main.cpp:24:
atlaspref.h:33:27: error: atlassettings.h: No such file or directory
weather_view.h:50: error: expected class-name before ‘{’ token
weather_view.h:54: error: ‘WFlags’ has not been declared
world_view.h:42: error: expected class-name before ‘{’ token
world_view.h:46: error: ‘WFlags’ has not been declared
research_view.h:37: error: expected class-name before ‘{’ token
research_view.h:41: error: ‘WFlags’ has not been declared
airport_view.h:47: error: expected class-name before ‘{’ token
airport_view.h:51: error: ‘WFlags’ has not been declared
kfreeflight_view.h:82: error: expected class-name before ‘{’ token
kfreeflight_view.h:86: error: ‘WFlags’ has not been declared
fgpref.h:34: error: expected class-name before ‘{’ token
fgpref.h:38: error: ‘WFlags’ has not been declared
fgprefbis.h:33: error: expected class-name before ‘{’ token
fgprefbis.h:37: error: ‘WFlags’ has not been declared
atlaspref.h:36: error: expected class-name before ‘{’ token
atlaspref.h:40: error: ‘WFlags’ has not been declared
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/doc/Desktop/kfreeflight-0.3.2/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.



Also noted that it again appears that a configure was completed before the 'make' process was started just as we saw before.

One of my first questions in this forum was to ask if anybody had been successful in getting Kfreeflight running with Flightgear in Ubuntu.....do you know if that has ever been done??

Do you think it would be of any value to go back to the developer with the last info gathered in the install process and see if the "errors' mean anything to him....
I am starting to believe the issue must be with the compatibility of Kfreeflight .....from his website I see there are 'packages' developed for CVS but nothing for Ubuntu.....

Hate to take your time away from your own products.....I know you can use some free time too....so dont feel bad to tell me I must remain a 'grasshopper'.....as one of the posts indicated about Kfreeflight.....a lot of errors....is it really worth it.....I would have hoped so....but am not getting a sign of the finish line.....

So what do think.....

Doc

---

### Post by Redeyes_Gambit on 2007-03-11
Hm. Well as for if anyone has ever gotten kfreeflight to work, I have no idea. However, because the developer has provided the source code it should be theoretically possible.

Lol, as for my free time and projects, a lot of it I have to sit here and wait for anyway. I'm currently getting a VMWared version of Ubuntu server 6.06 running. VMWare allows me to run an operating system INSIDE another operating system. So I' sitting here watching code scroll by in my virtual Ubuntu server, TRYING to get that driver I was telling you about to compile. I was trying to get it to work on a "real" machine, but it proved too much of a hassle to constantly jump back and forth between two real machines.

As for chatting with the developer, yea it might be a god idea to at least send him an e-mail asking what his take on the whole situation is. He certainly can't accuse us of not trying :) . If he does, just refer him here lol.

I'll tell you what, let me try to get kfreeflight to compile on MY machine, and if I can get it to then all I should have to do is send you a .deb of it and you can just double-click install it :D . I woulda done that to begin with if I had known I was gonna put you through the whole shebang lol.

---

### Post by lakedad on 2007-03-11
Will give the developer a shot of email.....he is in France and between his language barrier and mine it takes some doing to communicate...but he has been responsive....asks me questions that I cant answer.... I think he believes i understand Linux....it is worth a followup....will see what happens....

I would have thought many Ubuntu users would have Kfreeflight running as there must be a bunch of people that like flight simming (me for one) and FlightGear was one of the packages available to Ubuntu....Kfreeflight is a great looking 'GUI' for FlightGear.

You certainly dont have to apologize for putting me thru anything.....I think I owe you a bunch.....I have already learned a lot.....particularly about the 'dependency hell' place.:shock: 

I have only been using Ubuntu for a few weeks and it has been years since i had any form of a Linux package running....sort of got discouraged with some of the earlier distributions.....they demanded a lot of knowledge even to begin to learn it.....read books until I fell asleep most of the time.....so went back to Windows.

A side funny story.....as I mentioned I like flight simulators (the reason I stayed with Windows) and just recently updated my version of X-Plane 8.50 to version 8.60.... then found that i could only get X-Plane to run once without going back and deleting some files it was auto generating......got on their Forums and asked if anybody else was having this problem.....well there was one other guy....and it seems the root of the problem was that we both were running Windows ME.....

then I started to get questions 'worldwide' asking why i was still using Windows ME.....and the sales manager from X-Plane emailed me and informed me that Windows was so old they did not support it anymore and no it wouldn't work for me.....

when I questioned that the 'system requirements' for X-Plane noted only a "Windows OS" he said but they would not expect anybody to be using an out of date OS like Windows 95 etc.....  so now I find out that there are only two people in this world still running Windows ME....even though I have a copy of Windows XP I wont install it as i dont care to jump thru all the hoops to change over.....disk structure....drivers and old software that works for me but wont run on XP.....got to wonder why we bother with Windows.

I do like Ubuntu.....got to use it more and get to "depend" on it.....

Again thanks for your help.....I will give you an update after I hear from the developer....you can now return to your normal programs....:) 

i may still be the grasshopper but i think I might be able to turn into a "locust'

regards
doc

---

### Post by Redeyes_Gambit on 2007-03-11
Lol, yea windows does put one through a lot some times. Ubuntu to, just differently. 

Well it appears I have hit a bit of a serious snag on this end. You know how I was saying I was running an OS inside an OS using VMWare? Well apparently the tool I used to install VMWare with didn't finish the job (WHY OH WHY DIDN'T I USE SYNAPTIC!!?!?!?) and now every time I launch Synaptic it thinks I have a partially installed VMWare, and tries to correct the problem by running the install script. 

Thing is this blocks me from installing anything else (grr) and Synaptic can't finish installing VMWare either so I'm stuck in an endless loop trying to get VMWare to install (even though it already is.) I'll have to fix that before I can try compiling kfreeflight, but once that's done kfreeflight compile is next highest priority :) .

---

### Post by Redeyes_Gambit on 2007-03-11
Snag mended! That's what I love about Ubuntu. Even though it's not perfect (by nature no code is) when something goes wrong you get right to the heart of the problem and get it fixed in Ubuntu. In Windows that rarely happens -it's usually work-arounds or the three R's: Reboot, Reformat, Re-install.

Working on installing the dependencies and getting kfreeflight compiled now.

---

### Post by Redeyes_Gambit on 2007-03-11
Hm, looks like I won't be able to compile since I don't have flight simulator related stuff. I was hoping I could compile kfreeflight without having flightgear installed but it appears that is not so. I guess all hangs on the developer then.

---

### Post by lakedad on 2007-03-11
great to hear you got the 'loop' stopped and are moving on.....dont overworry the kfreeflight problem.....I will plod on and see what the developer has to say....

Hit one of my own 'snags'.....lost my email password(one of my hard drives died and of course I had a bunch of data unbacked :oops: )..... seems I have to know the secret name to get Earthlink to reset the password.... and dont have the original password to reset online....so now i will have to wait until tomorrow and call on the landline.....not fun dealing with telephone tech support.  :( 

Take the rest of the day off.....I am about to do just that....

best regards
doc

---

