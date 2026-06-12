---
title: "Trying to compile wesnoth - got stuck"
date: 2006-12-04
forum: General Help
---

### Post by tin2 on 2006-12-04
I am trying to compile wesnoth-1.1.11.

./configure --datadir=/usr/share/games/wesnoth/
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
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
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for ranlib... ranlib
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries /usr/X11R6/lib, headers
checking whether -R must be followed by a space... neither works
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for XOpenDisplay in -lX11... yes
checking for sdl-config... /usr/bin/sdl-config
checking for fribidi-config... no
configure: WARNING: *** FRIBIDI not found.
checking for libpng-config... no
checking for libpng12-config... no
checking for pkg-config... /usr/bin/pkg-config
Package libpng12 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libpng12.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libpng12' found
Package libpng12 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libpng12.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libpng12' found
checking for SDL - version >= 1.2.7... yes
checking for gnome-config... no
checking for kde-config... /usr/bin/kde-config
checking for libtool... /usr/bin/libtool
checking for IMG_Load in -lSDL_image... no
configure: error: *** SDL_image lib not found! Get SDL_image from
[http://www.libsdl.org/projects/SDL_image/index.html](http://www.libsdl.org/projects/SDL_image/index.html)

what do you think?

---

### Post by Edska on 2006-12-04
Try this

```
sudo apt-get install wesnoth wesnoth-ei wesnoth-httt wesnoth-music wesnoth-server wesnoth-sotbe wesnoth-trow
```

This will install newest (1.0.2) wesnoth without any compilation.
Personally I had the same problem. I installed that SDL libs. Use apt-get and install these: 
SDL
SDL-mixer
SDL-image
SDL-net
freetype2
freetype2-dev 

Try theses threats:
[http://ubuntuforums.org/showthread.php?t=312168&highlight=wesnoth+SDL]("http://ubuntuforums.org/showthread.php?t=312168&highlight=wesnoth+SDL")
[http://ubuntuforums.org/showthread.php?t=57183&highlight=wesnoth+SDL]("http://ubuntuforums.org/showthread.php?t=57183&highlight=wesnoth+SDL")

---

