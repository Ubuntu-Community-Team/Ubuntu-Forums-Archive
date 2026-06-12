---
title: "Can't find X includes"
date: 2007-02-05
forum: General Help
---

### Post by Dr Small on 2007-02-05
Hello, I've been trying to install some KDE apps on my Ubuntu PC, (which does have KDE) from KDE-Apps.org and just about everything I try to compile, it reads this error at the bottom:

> checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

I don't really understand what this means.
If anyone could help me, I'd appreciate it.

Dr Small

---

### Post by llamakc on 2007-02-05
On Ubuntu (and Debian-based distros) development packages are named *-dev, so the xserver-xorg package has a corresponding development package named xserver-xorg-dev. 

Install that, and see what the next (if any) error is.

```

Package: xserver-xorg-dev
Priority: optional
Section: x11
Installed-Size: 1628
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: i386
Source: xorg-server
Version: 1:1.1.1-0ubuntu12.1
Filename: pool/main/x/xorg-server/xserver-xorg-dev_1.1.1-0ubuntu12.1_i386.deb
Size: 297380
MD5sum: 850d9dffd59e990278c17a7621aee528
SHA1: 5f341a27b066ae3c90b50d114e81e8487ae0d616
SHA256: 3456a73abecf2170a5beae35d997168061850a167c6f62619ed65e282d0f6b71
Description: X.Org X server -- development files
 This package provides development files for the X.Org ('Xorg') X server.
 This is not quite the same as the DDK (Driver Development Kit) from the
 XFree86 4.x and X.Org 6.7, 6.8 and 6.9 series of servers; it provides
 headers and a pkg-config file for drivers using autotools to build
 against.
 .
 Unless you are developing or building a driver, you probably want
 xserver-xorg and/or xserver-xorg-core instead.

```

---

### Post by Dr Small on 2007-02-05
I installed "xserver-xorg-dev" via synaptic, and tried running ./configure again, and same error message...

* Dr Small tries a reboot.

Dr Small

---

### Post by Dr Small on 2007-02-05
Tried rebooting, and the problem still persists.


Dr Small

---

### Post by llamakc on 2007-02-05
FYI you didn't need to reboot. How about cut-pasting the last bit of the compile output in case it's sticking somewhere else too? And perhaps the exact package & version you are attempting to compile?

---

### Post by Dr Small on 2007-02-05
Attempting to compile: "kfreeflight-0.3.2"
./configure data:

> drsmall@drsmall:~/kfreeflight-0.3.2$ ./configure
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


Dr Small

---

### Post by llamakc on 2007-02-05
Looks like the xorg-dev has a BUNCH of depends that are *-dev packages, maybe that would help? I looked at KFreeFlight's mailing list and didn't see anything pertaining to your issue.

---

### Post by Dr Small on 2007-02-05
Ok. I installed xorg-dev and it got me a little bit further, I had another failure:

> configure: WARNING: libjpeg not found. disable JPEG support.

So I installed libjpeg and solved that problem, and the next one I can't figure out again, like usual:

> checking for Qt... configure: error: Qt (>= Qt 3.2 and < 4.0) (headers and libraries) not found. Please check your installation!

---

### Post by llamakc on 2007-02-05
Same problem as before: you need the *-dev packages.

```

apt-cache search qt |grep dev

```

Yikes, there's plenty of stuff returned by that. Perhaps it's kde-devel or libqt3-mt-dev or libqt4-dev?

---

### Post by Dr Small on 2007-02-05
This seems to be full of erros, no matter what I fix, or else I have very little things installed on my box :P
> checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

!!! I have KDE, but advatentally, i don't have some *-dev or something....
I'm beginning to wonder if this is actually worth of this...

Dr Small

---

### Post by macguyvok on 2007-09-06
Actually, I'm surprised no one answered this question for you. (I see it's pretty old, but I had to reply since the solution is pretty simple)

the package you need to install is:

 x11-dev

That will solve you problem. Though, you most likely need quite a bit more for whatever you're compiling. (For what I'm working on, I have reached the over 150 packages installed mark...)

Everytime you find an error, looks for that package's -dev version. For example, if it died on finding the KDE headers, look for kde-dev packages.

Good Luck!

--Chris

---

### Post by llamakc on 2007-09-06
There's no longer a package called x11-dev. There's an libx11-dev though. I've had no problems building packages with xorg-dev though, as mentioned in the first reply.

---

