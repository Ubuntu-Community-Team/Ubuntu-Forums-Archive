---
title: "Compiling problems...again..."
date: 2007-12-22
forum: General Help
---

### Post by Moonfrost on 2007-12-22
So I've been spending my afternoon today (nothing else to do and no money) trying to compile 2 programs...impossible is all I'm going to say after hours of frustration...
I enter into the folder I have on the desktop (in this case mednafen)...I type configure...well what do you know! command not found! okay so I drag the "configure" file which is inside the mednafen folder and it works...the problem here is, every time I type "make" (without quotes of course) it never does anything!!! so I try to find a file called "make" but on all the programs I tried before it's never there! so I've been in forums everywhere and all and can't find why is it only me that has this problems!!!! I never compiled anything successfully...why the hell are programmers so lazy to compile this themselves before releasing programs to the public??? I want help please if anybody can give it to me!!

I know I have to cd into the folder first by the way...

---

### Post by taurus on 2007-12-22
Assuming you are in the same directory of the source that you want to compile, you usually run

```
./configure
make
sudo make install
```
And before you compile anything, you need to install the build-essential package first.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by Moonfrost on 2007-12-22
> **taurus said:**
> Assuming you are in the same directory of the source that you want to compile, you usually run

```
./configure
make
sudo make install
```
And before you compile anything, you need to install the build-essential package first.

```
sudo apt-get update
sudo apt-get install build-essential
```

Yeah...I already knew all that but thanks a lot...make still doesn't work...maybe I need to specify something...tried it with 3 different programs I have to compile...

EDIT: Nevermind...it tells me that there's no directory specified (even though I'm in the folder itself) and then tells me that there's no makefile...in all the 3 programs I have tried today! is there a way to create a "make" file?

---

### Post by taurus on 2007-12-22
Why don't you post the whole error message with the command that you run?  Doesn't work is not really helping at all because nobody knows what's wrong with it to diagnose it.

./configure should create a Makefiles for you.

---

### Post by Moonfrost on 2007-12-22
> **taurus said:**
> Why don't you post the whole error message with the command that you run?  Doesn't work is not really helping at all because nobody knows what's wrong with it to diagnose it.

./configure should create a Makefiles for you.

Oh yeah sure...this is what comes out of ./configure (the usual stuff but there maybe something I don't know)...
```

gedg@gedg-desktop:~$ cd ~/Desktop/mednafen
gedg@gedg-desktop:~/Desktop/mednafen$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
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
checking how to run the C preprocessor... gcc -E
checking whether gcc and cc understand -c and -o together... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
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
checking for a BSD-compatible install... /usr/bin/install -c
checking for ptrdiff_t... yes
checking for size_t... yes
checking for short... yes
checking size of short... 2
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for long long... yes
checking size of long long... 8
checking for double... yes
checking size of double... 8
checking for __int64... no
checking size of __int64... 0
checking for void *... yes
checking size of void *... 4
checking for size_t... (cached) yes
checking size of size_t... 4
checking for ptrdiff_t... (cached) yes
checking size of ptrdiff_t... 4
checking for an ANSI C-conforming const... yes
checking for memcmp... yes
checking for memcpy... yes
checking for memmove... yes
checking for memset... yes
checking for mmap... yes
checking for munmap... yes
checking for madvise... yes
checking for signal... yes
checking for fcntl... yes
checking for getenv... yes
checking for putenv... yes
checking for setenv... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for mkdir... yes
checking for _mkdir... no
checking whether mkdir takes one argument... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking OpenGL/gl.h usability... no
checking OpenGL/gl.h presence... no
checking for OpenGL/gl.h... no
checking for X... libraries , headers 
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking whether we are using the GNU C Library 2 or newer... yes
checking for ranlib... (cached) ranlib
checking for simple visibility declarations... yes
checking for inline... inline
checking for stdint.h... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether integer division by zero raises SIGFPE... yes
checking for inttypes.h... yes
checking for unsigned long long int... yes
checking for inttypes.h... (cached) yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking whether imported symbols can be declared weak... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pthread_kill in -lpthread... yes
checking for pthread_rwlock_t... yes
checking for multithread API to use... posix
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking for inttypes.h... (cached) yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for getcwd... yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... yes
checking for munmap... (cached) yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for argz_count... yes
checking for argz_stringify... yes
checking for argz_next... yes
checking for __fsetlocking... yes
checking whether feof_unlocked is declared... yes
checking whether fgets_unlocked is declared... yes
checking for iconv... (cached) yes
checking for iconv declaration... (cached) 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for NL_LOCALE_NAME macro... yes
checking for bison... no
checking for long long int... yes
checking for long double... yes
checking for wchar_t... yes
checking for wint_t... yes
checking for intmax_t... yes
checking whether printf() supports POSIX/XSI format strings... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking for stdint.h... (cached) yes
checking for SIZE_MAX... (((1U << 31) - 1) * 2 + 1)
checking for stdint.h... (cached) yes
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for ptrdiff_t... (cached) yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for asprintf... yes
checking for fwprintf... yes
checking for putenv... (cached) yes
checking for setenv... (cached) yes
checking for setlocale... yes
checking for snprintf... yes
checking for wcslen... yes
checking whether _snprintf is declared... no
checking whether _snwprintf is declared... no
checking whether getc_unlocked is declared... yes
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for CFPreferencesCopyAppValue... (cached) no
checking for CFLocaleCopyCurrent... (cached) no
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for zlibVersion in -lz... yes
checking OPTIMIZER_FLAGS for gcc -fomit-frame-pointer... -fomit-frame-pointer
checking OPTIMIZER_FLAGS for gcc -finline-limit=6000... -finline-limit=6000
checking OPTIMIZER_FLAGS for gcc --param large-function-growth=800... --param large-function-growth=800
checking OPTIMIZER_FLAGS for gcc --param inline-unit-growth=175... --param inline-unit-growth=175
checking OPTIMIZER_FLAGS for gcc --param max-inline-insns-single=10000... --param max-inline-insns-single=10000
checking OPTIMIZER_FLAGS for gcc -fno-strict-overflow... no, unknown
checking WARNING_FLAGS for gcc -Wall... -Wall
checking WARNING_FLAGS for gcc -Winline... -Winline
checking WARNING_FLAGS for gcc -Wshadow... -Wshadow
checking GBA_EXTRA_FLAGS for gcc -fno-unit-at-a-time... -fno-unit-at-a-time
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.0... found.
checking for snd_ctl_open in -lasound... yes
checking for JACK... no
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for LIBCDIO... no
configure: error: *** libcdio not found!
```

the name of the application is "mednafen" and gedg is my username...

I noticed that libcdio is missing...this is an emulator which emulates multiple console and computer systems and some of them support the use of an original CD...I'm guessing I need that library just for that though and I don't think I need it in order to make it work at all...

this is the output of "make"

```
make: *** No targets specified and no makefile found.  Stop.

```

EDIT: oh yeah, mednafen is just an example...I get this with every single application I try to compile all the time...

EDIT 2: including mednafen of course...

---

### Post by taurus on 2007-12-22
If you look at the last few line of ./configure, there is an error message.

```

checking for libasound headers version >= 1.0.0... found.
checking for snd_ctl_open in -lasound... yes
checking for JACK... no
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
[B][COLOR="Blue"][SIZE="3"]checking for LIBCDIO... no
configure: error: *** libcdio not found![/SIZE][/COLOR][/B]

```
So, you need to install libcdio first before you run ./configure again.  And just so you know, once there is an error from ./configure, no need to even run _make_ because it will not work.  ./configure will create a Makefiles at the end only if it successfully finishes.

---

### Post by Moonfrost on 2007-12-22
> **taurus said:**
> If you look at the last few line of ./configure, there is an error message.

```

checking for libasound headers version >= 1.0.0... found.
checking for snd_ctl_open in -lasound... yes
checking for JACK... no
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
[B][COLOR="Blue"][SIZE="3"]checking for LIBCDIO... no
configure: error: *** libcdio not found![/SIZE][/COLOR][/B]

```
So, you need to install libcdio first before you run ./configure again.  And just so you know, once there is an error from ./configure, no need to even run _make_ because it will not work.  ./configure will create a Makefiles at the end only if it successfully finishes.

Ok thanks a lot and sorry for all the troubles...

---

### Post by Sef on 2007-12-22
> sorry for all the troubles...

Don't feel sorry.  You were smart to ask.  Please post any time that you have a question.

---

### Post by ~LoKe on 2007-12-22
And to save you some time...
```
sudo apt-get install libcdio-dev libcdio7
cd ~/Desktop/mednafen
./configure
make ## will only run if ./configure is successful
sudo make install ## will only run if make is successful
```

---

