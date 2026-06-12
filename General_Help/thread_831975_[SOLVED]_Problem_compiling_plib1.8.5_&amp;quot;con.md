---
title: "[SOLVED] Problem compiling plib1.8.5 &amp;quot;configure: error: could not find working GL lib"
date: 2008-06-17
forum: General Help
---

### Post by nugget659 on 2008-06-17
I am trying to compile the plib1.8.5

But ./configure fails with the following message:

```
checking for IceConnectionNumber in -lICE... yes
checking for pthread_create in -lpthread... no
checking for glNewList in -lGL... no
checking for glNewList in -lMesaGL... no
configure: error: could not find working GL library
```

I have the following packages installed:
ii  freeglut3                                  2.4.0-6
         OpenGL Utility Toolkit
ii  freeglut3-dev                              2.4.0-6
         OpenGL Utility Toolkit development files
ii  glutg3                                     3.7-25
         the OpenGL Utility Toolkit
ii  glutg3-dev                                 3.7-25
         the OpenGL Utility Toolkit development files
ii  libgl1-mesa-dev                            7.0.3~rc2-1ubuntu3
         A free implementation of the OpenGL API -- G
ii  libgl1-mesa-dri                            7.0.3~rc2-1ubuntu3
         A free implementation of the OpenGL API -- D
ii  libgl1-mesa-glx                            7.0.3~rc2-1ubuntu3
         A free implementation of the OpenGL API -- G
rc  libglew1.4                                 1.4.0-1ubuntu1
         The OpenGL Extension Wrangler - runtime envi
ii  libglew1.5                                 1.5.0dfsg1-3ubuntu1
         The OpenGL Extension Wrangler - runtime envi
ii  libglib2.0-0                               2.16.3-1ubuntu2
         The GLib library of C routines
ii  libglib2.0-cil                             2.12.0-2ubuntu3
         CLI binding for the GLib utility library 2.1
ii  libglibmm-2.4-1c2a                         2.16.0-1
         C++ wrapper for the GLib toolkit (shared lib
ii  libglu1-mesa                               7.0.3~rc2-1ubuntu3
         The OpenGL utility library (GLU)
ii  libglu1-mesa-dev                           7.0.3~rc2-1ubuntu3
         The OpenGL utility library -- development fi
ii  libglut3                                   3.7-25
         the OpenGL Utility Toolkit
ii  libglut3-dev                               3.7-25
         development libraries and headers for GLUT
ii  xlibmesa-gl-dev                            1:7.3+10ubuntu10
         transitional package for Debian etch
ii  xorg-driver-fglrx
1:7.1.0-8-3+2.6.24.13-18.41       Video driver for ATI graphics
accelerators
ii  xscreensaver-gl                            5.04-4ubuntu1
         GL(Mesa) screen hacks for xscreensaver
ii  xserver-xorg-video-glint                   1:1.1.1-8
         X.Org X server -- Glint display driver

I found this in config.log
```
configure:6841: checking for glNewList in -lGL
configure:6876: gcc -o conftest -g -O2    conftest.c -lGL    -lSM -lICE -lXi -lXmu -lXext -lX11  -lm >&5
/usr/bin/ld: cannot find -lXmu
collect2: ld returned 1 exit status
```

and this:
```
configure:6929: checking for glNewList in -lMesaGL
configure:6964: gcc -o conftest -g -O2    conftest.c -lMesaGL    -lSM -lICE -lXi -lXmu -lXext -lX11  -lm >&5
/usr/bin/ld: cannot find -lMesaGL
collect2: ld returned 1 exit status
```

In my searches, I found some suggestion that I should check for libGl.so
I found it in /usr/lib/
libGl.so is a link to libGl.so.1 which is a link to libGl.so.1.2

I also found a suggestion that I should try using:
./configure --with-lGL=/usr
but that failed, so I also tried:
./configure --with-lGL=/usr/
./configure --with-lGL=/usr/lib
./configure --with-lGL=/usr/lib/
all fail.

I am at a loss here. All of my searching has thus far failed to provide a solution. Help please. I have attached config.log in the hope that it can provide some useful information.

Thanks

---

### Post by nugget659 on 2008-06-19
This solved it:

```
sudo apt-get install libxmu-dev libxmu6
```

---

### Post by DynamicBits on 2009-05-05
Sorry to post to an older thread, but I had the same problem and this is the most recent thread I could find that is relevant.

I had the same problem with Xubuntu 9.04 (Jaunty) and plib-1.8.5. The above solution did not work for me. I created three symlinks that solved the problem:

```
sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so
sudo ln -s /usr/lib/libGLU.so.1 /usr/lib/libGLU.so
sudo ln -s /usr/lib/libXi.so.6 /usr/lib/libXi.so
```

I'm not sure if all three were required, but, with only the first two, I still got the error.


--
Andy

---

### Post by mallan157 on 2009-10-25
Likewise I still had this problem even after setting the symlinks as above (incidentally the first two already existed). I fixed it by installing libxmu-dev and libxmu-headers via Synaptic (libxmu6 was already installed). Don't know if both were needed, but they're small anyway.

---

### Post by HrachMD on 2010-01-10
Hi 
I also have problem with installing plib.
After forwarding by recomendations ./configure don't give error - not foun working GL
but this time another error - Can't find GL/gl.h. Look for Mesa devel packages for your distro.
???

---

### Post by joserc87 on 2011-12-05
Ok. This solutions doesnt work for me. I just solved by installing libxi-dev and libxine-dev and now it's compiling :D I don't know if the second one is neccesary, but it doesnt hurt...

Hope it helps!

---

