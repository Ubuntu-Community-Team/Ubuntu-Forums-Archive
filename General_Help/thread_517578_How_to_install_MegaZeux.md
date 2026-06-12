---
title: "How to install MegaZeux"
date: 2007-08-04
forum: General Help
---

### Post by mr.j on 2007-08-04
OK. I'm still new to linux and stuff, but I've had it for about a month and love it so here it goes.

I was trying to install MegaZeux, a game creation software. When I go into terminal and use the config.sh file and type the appropriate things i want like --platform linux to get a linux install (the software can go on a bunch of different OSs), it then tells me to type make.

When i do that i get a bunch of errors.

please help...

what i get when i type ./config.sh

justin@justinslinuxpartition:~/Desktop/mzx281g$ ./config.sh
usage: ./config.sh --platform [platform] <--prefix prefix>
                   <--sysconfdir sysconfdir> <option..>

 <prefix>        Where MegaZeux's dependencies should be found.
 <sysconfdir>    Where MegaZeux's config should be read from.

Supported [platform] values:

  win32          Microsoft Windows
  linux          Linux / BSD / Embedded
  macos          Macintosh OS X (not Classic)
  linux-static   Linux (statically linked)
  psp            Experimental PSP port
  mingw32        Use MinGW32 on Linux, to build for win32

Supported <option> values:
  --disable-x11     Disables X11, removing binary dependency.
  --enable-x11      Enables X11 support (default).

  --disable-gl      Disables all OpenGL renderers.
  --enable-gl       Enables OpenGL, runtime loaded (default).

  --disable-modplug Disables ModPlug music engine.
  --enable-modplug  Enables ModPlug music engine (default).

  --enable-mikmod   Enables MikMod music engine.
  --disable-mikmod  Disables MikMod music engine (default).

e.g.: ./config.sh --platform linux --prefix /usr
                  --sysconfdir /etc --disable-x11
e.g.: ./config.sh --platform win32

what i get when i type ./config.sh --platform linux --enable mikmod

justin@justinslinuxpartition:~/Desktop/mzx281g$ ./config/sh --platform linux --enable-mikmod
bash: ./config/sh: No such file or directory
justin@justinslinuxpartition:~/Desktop/mzx281g$ ./config.sh --platform linux --enable-mikmod
Building for platform:   linux
Using prefix:            /usr
Using sysconfdir:        /etc

X11 support enabled.
OpenGL support enabled.
Selected Modplug music engine.

Now type "make".

then when i type make

justin@justinslinuxpartition:~/Desktop/mzx281g$ make
cd contrib/libmodplug/src && make libs \
                                        BUILD=1 && cd ../../..
make[1]: Entering directory `/home/justin/Desktop/mzx281g/contrib/libmodplug/src'
g++ -O2 -Wall -DHAVE_INTTYPES_H -I. -Ilibmodplug -c fastmix.cpp -o fastmix.o
make[1]: g++: Command not found
make[1]: *** [fastmix.o] Error 127
make[1]: Leaving directory `/home/justin/Desktop/mzx281g/contrib/libmodplug/src'
make: *** [subdir] Error 2


please help me!

---

### Post by isaacj87 on 2007-08-04
My guess is that you're missing the development files for libmodplug.

Try going in to synaptic, search for libmodplug and install the package libmodplug-dev

P.S. If you don't have libmodplug installed you might want to install that too...;)

---

### Post by mr.j on 2007-08-05
Well I tried what you said.

I installed the development tools for the libmodplug, but i still got this after typing make.

justin@justinslinuxpartition:~/Desktop/mzx281g$ make
cd contrib/libmodplug/src && make libs \
                                        BUILD=1 && cd ../../..
make[1]: Entering directory `/home/justin/Desktop/mzx281g/contrib/libmodplug/src'
g++ -O2 -Wall -DHAVE_INTTYPES_H -I. -Ilibmodplug -c fastmix.cpp -o fastmix.o
make[1]: g++: Command not found
make[1]: *** [fastmix.o] Error 127
make[1]: Leaving directory `/home/justin/Desktop/mzx281g/contrib/libmodplug/src'
make: *** [subdir] Error 2
:(

---

