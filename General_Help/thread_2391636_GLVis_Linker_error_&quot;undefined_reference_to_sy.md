---
title: "GLVis: Linker error &quot;undefined reference to symbol 'XGetWindowAttributes'&quot;"
date: 2018-05-11
forum: General Help
---

### Post by staengsen on 2018-05-11
Hello experts,

I'm trying to install [GLVis]("http://glvis.org/") which has a lengthy list of dependencies (see end of post), all of which I installed, either via **apt-get** or manual compilation. However, I'm getting a linker error when trying to **make** GLVis. Specifically an *undefined reference to symbol 'XGetWindowAttributes'*: 

```
stan@ubuntu:~/Downloads/glvis-3.1$ make
g++ -O3 -I../mfem-3.3.2 -DGLVIS_MULTISAMPLE=4 -DGLVIS_MS_LINEWIDTH=1.4 -I/usr/include -DGLVIS_USE_LIBPNG -DGLVIS_USE_FREETYPE -I/usr/include/freetype2 -o glvis glvis.cpp -Llib -lglvis -L../mfem-3.3.2 -lmfem -lrt -L -lX11 -lGL -lGLU -lpng -lfreetype -lfontconfig -lpthread
/usr/bin/x86_64-linux-gnu-ld: lib/libglvis.a(aux_vis.o): undefined reference to symbol 'XGetWindowAttributes'
//usr/lib/x86_64-linux-gnu/libX11.so.6: error adding symbols: DSO missing from command line
collect2: error: ld returned 1 exit status
makefile:187: recipe for target 'glvis' failed
make: *** [glvis] Error 1

```
Make did not return any other errors, so that I assume I did not miss to provide any of the required libraries. After quite a bit of purging and reinstalling packages I chose to ask for your help, since I cannot even tell whether the fault is on my side of things. I have very little knowledge about the internals of Ubuntu and X11 and I'd be very appreciative of your kind help.

Is there something obvious I might have missed? This particular error has appeared for other people in contexts I cannot relate to and trying their solutions, if applicable, did not get me anywhere.

I'm on a virtual machine using Ubuntu 18.04 64bit.

Thank you.

---

The instructions for installing GLVis state:
> GLVis is an X11 application and can be built on Linux/Unix systems including
Mac OS X using the X11/XQuarz app and under Windows using Cygwin/X.

Besides a C++ compiler, GLVis depends on the following external packages:

- the MFEM library (use the latest release) plus any libraries that MFEM was
  built to depend on
  [http://mfem.org](http://mfem.org)

- the X11, GL and GLU libraries
  [http://www.x.org](http://www.x.org), [http://www.opengl.org](http://www.opengl.org), [http://www.mesa3d.org](http://www.mesa3d.org)

- the XQuarz app (on Mac OS X)
  [http://www.xquartz.org/](http://www.xquartz.org/)

- the libpng or libtiff library; used for taking screenshots (optional)
  [http://www.libpng.org](http://www.libpng.org), [http://www.libtiff.org](http://www.libtiff.org)

- the FreeType 2 and Fontconfig libraries; used for font rendering (optional)
  [http://www.freetype.org](http://www.freetype.org), [http://www.fontconfig.org](http://www.fontconfig.org)

- Cygwin/X (on Windows); install the packages xinit, libpng-devel,
  fontconfig-devel, libGLU-devel.
  [https://cygwin.com](https://cygwin.com), [https://x.cygwin.com](https://x.cygwin.com)

There are two build systems, one based on GNU make and one based on CMake, as
described below. Choose the one that matches the build system you used to
build MFEM.

---

### Post by ert on 2018-12-19
Don't know if this is still an issue, but I managed to solve the problem by removing  -L$(X11_LIB_DIR) in the variable GL_LIBS in makefile, line 121 . The problem is that $(X11_LIB_DIR) is empty and adding "-L " to the compiler/linker without argument masks the next library argument.

---

