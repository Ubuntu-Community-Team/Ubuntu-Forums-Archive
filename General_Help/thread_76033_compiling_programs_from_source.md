---
title: "compiling programs from source"
date: 2005-10-14
forum: General Help
---

### Post by fakie_flip on 2005-10-14
I have am having problems compiling programs from source in Ubuntu Linux 5.04 Hoary. Has anyone else had this problem? I installed g++ and it's dependencies from Synaptic. I use the commands ./configure, make and make install, but I get errors, and it does not work. I have reinstalled Ubuntu on my computer and still have the same thing, so I am sure other people have the same problem too.

---

### Post by Lord Illidan on 2005-10-14
Did you install build-essential?

sudo apt-get install build-essential

If yes, then can you specify the exact error...you know, copy and paste them here?

---

### Post by fakie_flip on 2005-10-15
[QUOTE=Lord Illidan]Did you install build-essential?

sudo apt-get install build-essential

If yes, then can you specify the exact error...you know, copy and paste them here?[/QUOTE]

I installed build-essential and got the same error. This time I noticed a message "configure: error: You need to install SDL (http://www.libsdl.org/)." I am going to install that and if that does not fix the problem, I will be back here to tell you what happened. Thanks.

chris@ubuntu:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
chris@ubuntu:~$ cd install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/
[email]chris@ubuntu:~/install/warzone2100-0.2.2.tar.bz[/email]2_FILES/warzone2100-0.2.2$ ls
AUTHORS       config.h.in  configure  depcomp     Makefile     missing
CHANGELOG     config.log   COPYING    install-sh  Makefile.in  README
config.guess  config.sub   data       lib         makerules    src
[email]chris@ubuntu:~/install/warzone2100-0.2.2.tar.bz[/email]2_FILES/warzone2100-0.2.2$ sudo ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ranlib... ranlib
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking whether closedir returns void... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for vprintf... yes
checking for _doprnt... no
checking for gethostname... yes
checking for memmove... yes
checking for memset... yes
checking for sqrt... no
checking for strchr... yes
checking for strdup... yes
checking for strncasecmp... yes
checking for strrchr... yes
checking for strstr... yes
checking for stdbool.h that conforms to C99... (cached) yes
checking for _Bool... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking for sdl-config... no
checking for SDL - version >= 1.1.4... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: You need to install SDL ([http://www.libsdl.org/)](http://www.libsdl.org/)).
[email]chris@ubuntu:~/install/warzone2100-0.2.2.tar.bz[/email]2_FILES/warzone2100-0.2.2$ make
make[1]: Entering directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/lib'
make[2]: Entering directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/lib/framework'
gcc -gstabs -DYY_STATIC -Wall -Wno-pointer-sign -g `sdl-config --cflags` -I .  -I ../../src -c -o block.o block.c
/bin/sh: sdl-config: command not found
cc1: error: unrecognized option `-Wno-pointer-sign'
make[2]: *** [block.o] Error 1
make[2]: Leaving directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/lib/framework'
make[2]: Entering directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/lib/gamelib'
gcc -gstabs -DYY_STATIC -Wall -Wno-pointer-sign -g `sdl-config --cflags` -I . -I ../framework -I ../sound -I ../ivis_opengl -I ../../src -c -o anim.o anim.c
/bin/sh: sdl-config: command not found
cc1: error: unrecognized option `-Wno-pointer-sign'
make[2]: *** [anim.o] Error 1
make[2]: Leaving directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/lib/gamelib'
make[2]: Entering directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/lib/netplay'
gcc -gstabs -DYY_STATIC -Wall -Wno-pointer-sign -g `sdl-config --cflags` -I . -I ../framework -I ../../src -c -o netaudio_stub.o netaudio_stub.c
/bin/sh: sdl-config: command not found
cc1: error: unrecognized option `-Wno-pointer-sign'
make[2]: *** [netaudio_stub.o] Error 1
make[2]: Leaving directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/lib/netplay'
make[2]: Entering directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/lib/script'
gcc -gstabs -DYY_STATIC -Wall -Wno-pointer-sign -g `sdl-config --cflags` -I . -I ../framework -I ../../src -c -o codeprint.o codeprint.c
/bin/sh: sdl-config: command not found
cc1: error: unrecognized option `-Wno-pointer-sign'
make[2]: *** [codeprint.o] Error 1
make[2]: Leaving directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/lib/script'
make[2]: Entering directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/lib/sequence'
gcc -gstabs -DYY_STATIC -Wall -Wno-pointer-sign -g `sdl-config --cflags` -I . -I ../framework -I ../../src -c -o adpcm.o adpcm.c
/bin/sh: sdl-config: command not found
cc1: error: unrecognized option `-Wno-pointer-sign'
make[2]: *** [adpcm.o] Error 1
make[2]: Leaving directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/lib/sequence'
make[2]: Entering directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/lib/sound'
gcc -gstabs -DYY_STATIC -Wall -Wno-pointer-sign -g `sdl-config --cflags` -I . -I ../framework -I ../gamelib -I ../ivis_opengl -I ../../src -c -o audio.o audio.c/bin/sh: sdl-config: command not found
cc1: error: unrecognized option `-Wno-pointer-sign'
make[2]: *** [audio.o] Error 1
make[2]: Leaving directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/lib/sound'
make[2]: Entering directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/lib/widget'
gcc -gstabs -DYY_STATIC -Wall -Wno-pointer-sign -g `sdl-config --cflags` -I . -I ../framework -I ../ivis_opengl -I ../../src -c -o bar.o bar.c
/bin/sh: sdl-config: command not found
cc1: error: unrecognized option `-Wno-pointer-sign'
make[2]: *** [bar.o] Error 1
make[2]: Leaving directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/lib/widget'
make[2]: Entering directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/lib/ivis_opengl'
gcc -gstabs -DYY_STATIC -Wall -Wno-pointer-sign -g `sdl-config --cflags` -I . -I ../framework -I ../gamelib -I ../../src -c -o bitimage.o bitimage.c
/bin/sh: sdl-config: command not found
cc1: error: unrecognized option `-Wno-pointer-sign'
make[2]: *** [bitimage.o] Error 1
make[2]: Leaving directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/lib/ivis_opengl'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/lib'
make[1]: svnversion: Command not found
make[1]: Entering directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/src'
gcc -gstabs -DYY_STATIC -Wall -Wno-pointer-sign -g -I . `sdl-config --cflags` -I ../lib/framework -I ../lib/gamelib -I ../lib/netplay -I ../lib/script -I ../lib/sequence -I ../lib/sound -I ../lib/widget -I ../lib/ivis_opengl -DSVN_REVISION=\"\"  -c -o ai.o ai.c
/bin/sh: sdl-config: command not found
cc1: error: unrecognized option `-Wno-pointer-sign'
make[1]: *** [ai.o] Error 1
make[1]: Leaving directory `/home/chris/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2/src'
make: *** [all] Error 2
chris@ubuntu:~/install/warzone2100-0.2.2.tar.bz2_FILES/warzone2100-0.2.2$

---

### Post by fakie_flip on 2005-10-15
I went to that website for sdl library. I clicked on downloadable, and it took me to documentation. I am not sure where to download it at. I already looked in Synaptic, and it is not there. What should I do?  I found several files that had libsdl in their names, but I did not know which one to get.

---

### Post by fakie_flip on 2005-10-15
I installed libsdl-dev and libsdl-net. That seemed to fix some of the problems. Now I have a new one when I try to run configure. Look down towards the bottom. I get several errors about OpenAL.

[email]chris@ubuntu:~/install/warzone2100-0.2.2.tar.bz[/email]2_FILES/warzone2100-0.2.2$ sudo ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ranlib... ranlib
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking whether closedir returns void... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for vprintf... yes
checking for _doprnt... no
checking for gethostname... yes
checking for memmove... yes
checking for memset... yes
checking for sqrt... no
checking for strchr... yes
checking for strdup... yes
checking for strncasecmp... yes
checking for strrchr... yes
checking for strstr... yes
checking for stdbool.h that conforms to C99... (cached) yes
checking for _Bool... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.1.4... yes
checking for presence of SDL_net... Found SDL_net in path
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking for main in -lGL... yes
checking OpenGL... yes
checking AL/al.h usability... no
checking AL/al.h presence... no
checking for AL/al.h... no
checking for main in -lopenal... no
checking for main in -lopenal32... no
checking for main in -lalut... no
checking OpenAL... no
configure: error: OpenAL is currently mandatory
[email]chris@ubuntu:~/install/warzone2100-0.2.2.tar.bz[/email]2_FILES/warzone2100-0.2.2$

---

### Post by az on 2005-10-15
Install libopenal-dev

---

### Post by fakie_flip on 2005-10-15
[QUOTE=azz]Install libopenal-dev[/QUOTE]

I looked in Synaptic and found that. I already have that. The version I have is 0.2004090900-1.1. I also have lots of other libopenal packages installed.

---

