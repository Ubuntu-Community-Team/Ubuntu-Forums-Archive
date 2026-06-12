---
title: "The OpenGL library (libGL.so)"
date: 2008-02-17
forum: General Help
---

### Post by UK-Wobbie on 2008-02-17
Do any one know where i can get "The OpenGL library" (libGL.so) from? :)
It's for lxdream, In the setup it need's it to run.

---

### Post by zvacet on 2008-02-17
Did you tried 

```
sudo apt-get build-dep lxdream
```

from directory where lxdream source is.You can try this too 

```
sudo apt-get install auto-apt
sudo auto-apt update
sudo auto-apt updatedb && sudo auto-apt update-local
```

When you are finish run in foldet from wich you are compiling

```
sudo auto-apt run ./configure
```

---

### Post by UK-Wobbie on 2008-02-17
> **zvacet said:**
> Did you tried 

```
sudo apt-get build-dep lxdream
```

from directory where lxdream source is.You can try this too 

```
sudo apt-get install auto-apt
sudo auto-apt update
sudo auto-apt updatedb && sudo auto-apt update-local
```

When you are finish run in foldet from wich you are compiling

```
sudo auto-apt run ./configure
```

OK thanks i give it a go :)

---

### Post by UK-Wobbie on 2008-02-17
It come out with the same thing

rwaller@Ubuntu:~# sudo auto-apt run /home/rwaller/Desktop/lxdream-0.8.3/configure
Entering auto-apt mode:/home/rwaller/Desktop/lxdream-0.8.3/configure
Exit the command to leave auto-apt mode.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking Carbon/Carbon.h usability... no
checking Carbon/Carbon.h presence... no
checking for Carbon/Carbon.h... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBPNG... yes
checking for uncompress in -lz... yes
checking for glXQueryVersion in -lGL... no
The OpenGL library (libGL.so) could not be found, but is required.

It needs The OpenGL library (libGL.so) :(

---

### Post by fiprojects on 2008-02-17
I have the same problem and wonder what your solution is/was... I have Ubuntu 7.10 and installed a variety of web design programs to check them out.  Amaya did start up at one point but then stopped working.  I looked at the properties of the icon and found out the binary it wanted to startup so I did it manually from the command line and got the following:

amaya: error while loading shared libraries: libGL.so.1: 

I have uninstalled and re-installed Amaya using Synaptic but its the same thing each time.  I have searched for libGL and find references to installing libgl1-mesa-swx11 but when I request to install that it wants to install ubuntu-desktop

Anyone got any ideas?

---

### Post by UK-Wobbie on 2008-02-17
> **fiprojects said:**
> I have the same problem and wonder what your solution is/was... I have Ubuntu 7.10 and installed a variety of web design programs to check them out.  Amaya did start up at one point but then stopped working.  I looked at the properties of the icon and found out the binary it wanted to startup so I did it manually from the command line and got the following:

amaya: error while loading shared libraries: libGL.so.1: 

I have uninstalled and re-installed Amaya using Synaptic but its the same thing each time.  I have searched for libGL and find references to installing libgl1-mesa-swx11 but when I request to install that it wants to install ubuntu-desktop

Anyone got any ideas?

Well am still looking for "libGL.so"
So Welcome to the Game :lolflag:
I seen this [http://hany.sk/~hany/RPM/libGL.so.1.html](http://hany.sk/~hany/RPM/libGL.so.1.html)
Do not know if that as got anything to do with it in anyway. :confused:

---

### Post by UK-Wobbie on 2008-02-17
> **fiprojects said:**
> I have the same problem and wonder what your solution is/was... I have Ubuntu 7.10 and installed a variety of web design programs to check them out.  Amaya did start up at one point but then stopped working.  I looked at the properties of the icon and found out the binary it wanted to startup so I did it manually from the command line and got the following:

amaya: error while loading shared libraries: libGL.so.1: 

I have uninstalled and re-installed Amaya using Synaptic but its the same thing each time.  I have searched for libGL and find references to installing libgl1-mesa-swx11 but when I request to install that it wants to install ubuntu-desktop

Anyone got any ideas?

Hey when you put "libgl1-mesa-swx11" And i looked in Synaptic Package Manager lol That is Mesa!

Mesa-3.4-5.i586  ->	A 3-D graphics library similar to OpenGL

Look at this [http://hany.sk/~hany/RPM/libGL.so.1.html](http://hany.sk/~hany/RPM/libGL.so.1.html)

---

