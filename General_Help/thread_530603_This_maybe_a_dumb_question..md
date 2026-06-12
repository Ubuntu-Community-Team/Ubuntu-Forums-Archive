---
title: "This maybe a dumb question."
date: 2007-08-20
forum: General Help
---

### Post by iason on 2007-08-20
i want to install ubuntu server and run assaultcube, I dont want xwin and all that gui stuff from the desktop install.   Can this be done? I've tried compiling with no luck after thinking I had all the dependencies installed.  My goal is just to get it up and running it as a game server.

I've tried both the desktop and the server distro.  I am going to reinstall the server when I get home and try the .deb pkg from getdeb.com and see if that makes any difference?   Anyone have any suggestions?

below is the error im getting when trying to compile the src, I see SDL errors there, but i know SDL is installed

iason@claud:~/iason/AssaultCube/source/src$ sudo make install
Password:
make -C ../enet all
make[1]: Entering directory `/home/iason/iason/AssaultCube/source/enet'
Making all in include
make[2]: Entering directory `/home/iason/iason/AssaultCube/source/enet/include'
Making all in enet
make[3]: Entering directory `/home/iason/iason/AssaultCube/source/enet/include/enet'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/iason/iason/AssaultCube/source/enet/include/enet'
make[3]: Entering directory `/home/iason/iason/AssaultCube/source/enet/include'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/iason/iason/AssaultCube/source/enet/include'
make[2]: Leaving directory `/home/iason/iason/AssaultCube/source/enet/include'
make[2]: Entering directory `/home/iason/iason/AssaultCube/source/enet'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/iason/iason/AssaultCube/source/enet'
make[1]: Leaving directory `/home/iason/iason/AssaultCube/source/enet'
g++ -O3 -fomit-frame-pointer -I/usr/X11R6/include -I../enet/include `sdl-config --cflags` -fsigned-char -Wall -Wno-deprecated -c -o console.o console.cpp
console.cpp: In function âvoid pasteconsole()â:
console.cpp:192: error: âstruct SDL_SysWMinfoâ has no member named âsubsystemâ
console.cpp:192: error: âSDL_SYSWM_X11â was not declared in this scope
console.cpp:195: error: âstruct SDL_SysWMinfoâ has no member named âinfoâ
console.cpp: At global scope:
console.cpp:22: warning: â__dummy_setconskipâ defined but not used
console.cpp:60: warning: â__dummy_toggleconsoleâ defined but not used
console.cpp:115: warning: â__dummy_keymapâ defined but not used
console.cpp:130: warning: â__dummy_bindkeyâ defined but not used
console.cpp:153: warning: â__dummy_onreleaseâ defined but not used
console.cpp:168: warning: â__dummy_saycommandâ defined but not used
console.cpp:169: warning: â__dummy_mapmsgâ defined but not used
console.cpp:227: warning: â__dummy_historyâ defined but not used
make: *** [console.o] Error 1

---

### Post by noerrorsfound on 2007-08-26
You have to install the development libraries of SDL, as well.
> Unix users need to make sure to have the development version of all libs
installed (OpenGL, SDL, SDL_Mixer, SDL_Image, zlib, libpng). The included
makefiles can be used to build.
Make sure you have all the libraries from above.

---

