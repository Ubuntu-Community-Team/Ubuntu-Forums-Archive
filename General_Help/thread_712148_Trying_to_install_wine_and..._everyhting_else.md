---
title: "Trying to install wine and... everyhting else"
date: 2008-03-01
forum: General Help
---

### Post by bobmart32 on 2008-03-01
Ok, I'm a nnob at Linux and I must say, I LOVE IT. Only one problem thus far: Installing Wine I'm trying to get this program wine to work and everytime I run ./configure I get message that says: "No suitable flex found, please install the Flex package". So, I run "get flex" in the terminal and come up with(and I'm paraphrasing here because I can't remember word-for-word) "Flex not found, however, it is mentioned. File is probably corrupt, invalid, or missing. No Flex installation candidate". I have also tried to run Bison 2.1 and what seems to be a flex package on my computer and it still won't work. 

Here is the whole Log:

```
/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1768: creating cache config.cache
configure:2100: checking build system type
configure:2118: result: i686-pc-linux-gnu
configure:2140: checking host system type
configure:2155: result: i686-pc-linux-gnu
configure:2221: checking whether make sets $(MAKE)
configure:2242: result: yes
configure:2299: checking for gcc
configure:2315: found /usr/bin/gcc
configure:2326: result: gcc
configure:2564: checking for C compiler version
configure:2571: gcc --version >&5
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2574: $? = 0
configure:2581: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
configure:2584: $? = 0
configure:2591: gcc -V >&5
gcc: '-V' option must have argument
configure:2594: $? = 1
configure:2617: checking for C compiler default output file name
configure:2644: gcc    conftest.c  >&5
configure:2647: $? = 0
configure:2685: result: a.out
configure:2702: checking whether the C compiler works
configure:2712: ./a.out
configure:2715: $? = 0
configure:2732: result: yes
configure:2739: checking whether we are cross compiling
configure:2741: result: no
configure:2744: checking for suffix of executables
configure:2751: gcc -o conftest    conftest.c  >&5
configure:2754: $? = 0
configure:2778: result: 
configure:2784: checking for suffix of object files
configure:2810: gcc -c   conftest.c >&5
configure:2813: $? = 0
configure:2836: result: o
configure:2840: checking whether we are using the GNU C compiler
configure:2869: gcc -c   conftest.c >&5
configure:2875: $? = 0
configure:2892: result: yes
configure:2897: checking whether gcc accepts -g
configure:2927: gcc -c -g  conftest.c >&5
configure:2933: $? = 0
configure:3032: result: yes
configure:3049: checking for gcc option to accept ISO C89
configure:3123: gcc  -c -g -O2  conftest.c >&5
configure:3129: $? = 0
configure:3152: result: none needed
configure:3228: checking for g++
configure:3244: found /usr/bin/g++
configure:3255: result: g++
configure:3286: checking for C++ compiler version
configure:3293: g++ --version >&5
g++ (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3296: $? = 0
configure:3303: g++ -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
configure:3306: $? = 0
configure:3313: g++ -V >&5
g++: '-V' option must have argument
configure:3316: $? = 1
configure:3319: checking whether we are using the GNU C++ compiler
configure:3348: g++ -c   conftest.cpp >&5
configure:3354: $? = 0
configure:3371: result: yes
configure:3376: checking whether g++ accepts -g
configure:3406: g++ -c -g  conftest.cpp >&5
configure:3412: $? = 0
configure:3511: result: yes
configure:3577: checking for cpp
configure:3593: found /usr/bin/cpp
configure:3604: result: cpp
configure:3631: checking for the directory containing the Wine tools
configure:3655: result: $(TOPOBJDIR)
configure:3666: checking how to run the C preprocessor
configure:3706: gcc -E  conftest.c
configure:3712: $? = 0
configure:3743: gcc -E  conftest.c
conftest.c:8:28: error: ac_nonexistent.h: No such file or directory
configure:3749: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "Wine"
| #define PACKAGE_TARNAME "wine"
| #define PACKAGE_VERSION "0.9.54"
| #define PACKAGE_STRING "Wine 0.9.54"
| #define PACKAGE_BUGREPORT "wine-devel@winehq.org"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:3782: result: gcc -E
configure:3811: gcc -E  conftest.c
configure:3817: $? = 0
configure:3848: gcc -E  conftest.c
conftest.c:8:28: error: ac_nonexistent.h: No such file or directory
configure:3854: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "Wine"
| #define PACKAGE_TARNAME "wine"
| #define PACKAGE_VERSION "0.9.54"
| #define PACKAGE_STRING "Wine 0.9.54"
| #define PACKAGE_BUGREPORT "wine-devel@winehq.org"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:3892: checking for X
configure:4062: gcc -o conftest -g -O2   conftest.c -lX11  >&5
conftest.c:8:22: error: X11/Xlib.h: No such file or directory
configure:4068: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "Wine"
| #define PACKAGE_TARNAME "wine"
| #define PACKAGE_VERSION "0.9.54"
| #define PACKAGE_STRING "Wine 0.9.54"
| #define PACKAGE_BUGREPORT "wine-devel@winehq.org"
| /* end confdefs.h.  */
| #include <X11/Xlib.h>
| int
| main ()
| {
| XrmInitialize ()
|   ;
|   return 0;
| }
configure:4116: result: no
configure:5211: checking for flex
configure:5241: result: no
configure:5252: error: no suitable flex found. Please install the 'flex' package.

```

Some notes about my system:

Ubuntu Gutsy 7.10
Processezor: Intel
Laptop: Gateway
OS: Can Dual-boot with either Windows XP or Ubuntu Gutsy.

Will someone help me? :(

---

### Post by sumguy231 on 2008-03-01
If you want the latest version of Wine, just use the winehq repository to install it:
[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

With most common applications like Wine, you should never have to compile them by hand. You should check to see if you can use the package manager first.

Oh, and by the way, there is a nice graphical package manager at System -> Administration -> Synaptic Package Manager. Or you can use apt-get from the terminal.

---

### Post by bobmart32 on 2008-03-01
only problem with that is that, I don't have internet eith the linux. That is why I need wine because its windiws-based. 2nd I downloaded many different versions of wine, including the latest version. I still get the same message :( 

I have looked at the Synaptic PAckage manager before. I'll try that but, I'm not sure how to use. Its a bit confusing...

Thank you!

---

### Post by sumguy231 on 2008-03-01
Synaptic also requires an Internet connection.

You might also find it easier to download the .deb packages for Wine where you have access to the Internet, and then carry them over to the Ubuntu system. There, just double-click to install them. Make sure you have all the dependency packages as well. You can download Wine and all of its dependencies here:
[http://packages.ubuntu.com/gutsy/wine](http://packages.ubuntu.com/gutsy/wine)

Honestly, if you can't get an Internet connection working with Ubuntu I would suggest a different operating system which is more friendly to being offline all the time.

---

### Post by bobmart32 on 2008-03-01
My internet is windows based. I'm using the All-Tel, Evdo-USB modem to get internet. I'm hoping wine will let me get internet on linux but, in the case it doesn't, is there anyhitng I can do to get my internet to work?

---

### Post by sumguy231 on 2008-03-01
Wine won't help you get your Windows-only modem to work in Ubuntu, but there might still be a way. Does your modem seriously not have an ethernet port?

---

### Post by bobmart32 on 2008-03-01
Ahh, yes, it has ethernet!

---

### Post by sumguy231 on 2008-03-01
Good then, assuming your computer has an ethernet port, it is almost certainly supported by Ubuntu.

---

### Post by zaid0 on 2008-03-06
im jus at noob. how?what? is apt get terminal.
how to open a window?

---

### Post by chewearn on 2008-03-06
> **zaid0 said:**
> im jus at noob. how?what? is apt get terminal.
how to open a window?
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

