---
title: "need help installing freedriodrpg-0.10.1"
date: 2007-05-24
forum: General Help
---

### Post by pwgthegreat on 2007-05-24
hi,
I am new to linux and learning a lot of cool stuff but I need help installing  a game called freedroidrpg-0.10.1.  fixed some of the problems by reading forums.  still haveing problem with 
the . /configure command . 

I installed  libvorbisfile-ruby 1.8 and libgtk1.2-dev from the package manager and gave me this

```
root@blacktiger-desktop:~/freedroidrpg-0.10.1# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
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
checking whether make sets $(MAKE)... (cached) yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sin in -lm... yes
checking for X... no
configure: Checking for compulsory SDL libraries:
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.3... yes
checking for jpeg_start_compress in -ljpeg... yes
checking for compress in -lz... yes
checking for png_read_png in -lpng... yes
checking for IMG_LoadJPG_RW in -lSDL_image... yes
checking for SDLNet_Init in -lSDL_net... yes
configure: Checking for optional SDL libraries:
checking for Mix_ChannelFinished in -lSDL_mixer... no
configure: WARNING: libSDL_mixer not found!
you need the SDL_mixer library (version >= 1.2.1) if you want sound!
(see see http://www.libsdl.org/)
--> compiling without sound support
checking for oggpack_read in -logg... yes
checking for vorbis_block_init in -lvorbis... no
configure: WARNING:
--------------------------------------------------
libvorbis not found!
You need the Vorbis libs installed if you want
Freedroid to be able to play Ogg files (e.g. the Intro theme)
--------------------------------------------------
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking for cc_r... gcc
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking whether we are using the Microsoft C compiler... no
checking windows.h usability... no
checking windows.h presence... no
checking for windows.h... no
checking for OpenGL library... -lGL
checking for openGL libraries... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking for unistd.h... (cached) yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking execinfo.h usability... yes
checking execinfo.h presence... yes
checking for execinfo.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking return type of signal handlers... void
checking for alarm... yes
checking for getcwd... yes
checking for gettimeofday... yes
checking for memset... yes
checking for sqrt... yes
checking for strstr... yes
checking for strtok... yes
checking for alphasort... yes
checking for scandir... yes
checking for backtrace... yes
checking for gtk-config... /usr/bin/gtk-config
checking for GTK - version >= 1.2.0... no
*** Could not run GTK test program, checking why...
*** The test program compiled, but did not run. This usually means
*** that the run-time linker is not finding GTK or finding the wrong
*** version of GTK. If it is not finding GTK, you'll need to set your
*** LD_LIBRARY_PATH environment variable, or edit /etc/ld.so.conf to point
*** to the installed location  Also, make sure you have run ldconfig if that
*** is required on your system
***
*** If you have an old version installed, it is best to remove it, although
*** you may also be able to get things to work by modifying LD_LIBRARY_PATH
***
*** If you have a RedHat 5.0 system, you should remove the GTK package that
*** came with the system with the command
***
***    rpm --erase --nodeps gtk gtk-devel
configure: WARNING:
--------------------------------------------------
WARNING: You need libgtk-dev >= 1.20 in order to
be able to build the ItemEditor!

If you only want to play Freedroid you can ignore this!
--------------------------------------------------
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating croppy/Makefile
config.status: creating win32/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

```

thanks for all the help you can give !!!

---

