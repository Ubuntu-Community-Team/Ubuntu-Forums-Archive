---
title: "Compiling from Source"
date: 2007-07-22
forum: General Help
---

### Post by linuxnovice on 2007-07-22
Hi,

I need a program called Gazebo and its associated Player & Stage for my research. Info about these can be found here:

[http://playerstage.sourceforge.net/doc/Gazebo-manual-0.5-html/index.html](http://playerstage.sourceforge.net/doc/Gazebo-manual-0.5-html/index.html)

I am trying to install these on my Laptop. Gazebo has ODE (Open Dynamics Library) as a pre-requisite. So I downloaded the source for that and ran the configure script. Nothing went wrong and I was ready to do a make. This is what I got from configure and make:

Configure:

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /home/sudarshan/Gazebo: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking whether byte ordering is bigendian... no
checking for X... libraries , headers
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking whether make sets $(MAKE)... (cached) yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for windres... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for working volatile... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for ranlib... ranlib
checking for size_t... yes
checking if a soname should be set... no
checking if tests should be built... yes
checking alloca.h usability... yes
checking alloca.h presence... yes
checking for alloca.h... yes
checking ieeefp.h usability... no
checking ieeefp.h presence... no
checking for ieeefp.h... no
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for stdlib.h... (cached) yes
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
checking for string.h... (cached) yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking values.h usability... yes
checking values.h presence... yes
checking for values.h... yes
checking float.h usability... yes
checking float.h presence... yes
checking for float.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking if gyroscopic term should be used... yes
checking if double precision is requested... no
checking for appropriate dInfinity constant... FLT_MAX
checking for float.h... (cached) yes
checking for appropriate dEpsilon constant... FLT_EPSILON
checking for a Pentium CPU... yes
checking for a x86-64 CPU... no
checking if building a release library... no
checking if building a debug library... no
checking for char... yes
checking size of char... 1
checking for int... yes
checking size of int... 4
checking for short... yes
checking size of short... 2
checking for long int... yes
checking size of long int... 4
checking for void*... yes
checking size of void*... 4
checking which drawstuff lib to build... X11
checking for the suffix of shared libraries... .so
checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
checking for main in -lopengl32... no
checking for main in -lglu32... no
checking for main in -lXmu... yes
checking for main in -lXi... yes
checking for main in -lX... no
checking for main in -lX11... yes
checking for main in -lcomctl32... no
checking for main in -lkernel32... no
checking for main in -luser32... no
checking for main in -lgdi32... no
checking for main in -lwinmm... no
checking for main in -lstdc++... yes
checking for main in -lm... yes
checking for main in -lpthread... yes
checking for gprof... no
checking for floor... yes
checking for memmove... yes
checking for memset... yes
checking for select... yes
checking for sqrt... yes
checking for sqrtf... yes
checking for sinf... yes
checking for cosf... yes
checking for fabsf... yes
checking for atan2f... yes
checking for fmodf... yes
checking for copysignf... yes
checking for copysign... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for gettimeofday... yes
checking for isnan... yes
checking for isnanf... yes
checking for _isnan... no
checking for _isnanf... no
checking for __isnan... yes
checking for __isnanf... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for obstacks... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking for vprintf... yes
checking for _doprnt... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating include/Makefile
config.status: creating include/ode/Makefile
config.status: creating ode/Makefile
config.status: creating ode/src/Makefile
config.status: creating drawstuff/Makefile
config.status: creating drawstuff/src/Makefile
config.status: creating drawstuff/dstest/Makefile
config.status: creating ode/test/Makefile
config.status: creating ode-config
config.status: creating include/ode/config.h
config.status: include/ode/config.h is unchanged
config.status: executing depfiles commands
Configuration:
  Target system type:      i686-pc-linux-gnu
  Build  system type:      i686-pc-linux-gnu
  Host   system type:      i686-pc-linux-gnu
  Use double precision:    no
  Use OPCODE:              yes
  Use GIMPACT:             no
  Use gyroscopic term:     yes
  Is this a Pentium:       yes
  Is the CPU x86-64:       no
  Is this a release build: no
  Is this a debug build:   no
  Using SONAME:           no
  Headers will be installed in /usr/local/include/ode
  Libraries will be installed in /usr/local/lib

make:
sudarshan@Lucky-Linux:~/Gazebo Help/ode-0.8$ make
Making all in include
make[1]: Entering directory `/home/sudarshan/Gazebo Help/ode-0.8/include'
Making all in ode
make[2]: Entering directory `/home/sudarshan/Gazebo Help/ode-0.8/include/ode'
make  all-am
make[3]: Entering directory `/home/sudarshan/Gazebo Help/ode-0.8/include/ode'
make[3]: Leaving directory `/home/sudarshan/Gazebo Help/ode-0.8/include/ode'
make[2]: Leaving directory `/home/sudarshan/Gazebo Help/ode-0.8/include/ode'
make[2]: Entering directory `/home/sudarshan/Gazebo Help/ode-0.8/include'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/sudarshan/Gazebo Help/ode-0.8/include'
make[1]: Leaving directory `/home/sudarshan/Gazebo Help/ode-0.8/include'
Making all in drawstuff
make[1]: Entering directory `/home/sudarshan/Gazebo Help/ode-0.8/drawstuff'
Making all in src
make[2]: Entering directory `/home/sudarshan/Gazebo Help/ode-0.8/drawstuff/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I../../include/ode    -I../../include -I../../include -g -O2 -I -L -MT libdrawstuff_a-drawstuff.o -MD -MP -MF ".deps/libdrawstuff_a-drawstuff.Tpo" -c -o libdrawstuff_a-drawstuff.o `test -f 'drawstuff.cpp' || echo './'`drawstuff.cpp; \
        then mv -f ".deps/libdrawstuff_a-drawstuff.Tpo" ".deps/libdrawstuff_a-drawstuff.Po"; else rm -f ".deps/libdrawstuff_a-drawstuff.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../include/ode    -I../../include -I../../include -g -O2 -I -L -MT libdrawstuff_a-x11.o -MD -MP -MF ".deps/libdrawstuff_a-x11.Tpo" -c -o libdrawstuff_a-x11.o `test -f 'x11.cpp' || echo './'`x11.cpp; \
        then mv -f ".deps/libdrawstuff_a-x11.Tpo" ".deps/libdrawstuff_a-x11.Po"; else rm -f ".deps/libdrawstuff_a-x11.Tpo"; exit 1; fi
rm -f libdrawstuff.a
ar cru libdrawstuff.a libdrawstuff_a-drawstuff.o  libdrawstuff_a-x11.o
ranlib libdrawstuff.a
make[2]: Leaving directory `/home/sudarshan/Gazebo Help/ode-0.8/drawstuff/src'
Making all in dstest
make[2]: Entering directory `/home/sudarshan/Gazebo Help/ode-0.8/drawstuff/dstest'
if g++ -DHAVE_CONFIG_H -I. -I. -I../../include/ode    -I../../include -I../.. -g -O2 -I -L -MT dstest-dstest.o -MD -MP -MF ".deps/dstest-dstest.Tpo" -c -o dstest-dstest.o `test -f 'dstest.cpp' || echo './'`dstest.cpp; \
        then mv -f ".deps/dstest-dstest.Tpo" ".deps/dstest-dstest.Po"; else rm -f ".deps/dstest-dstest.Tpo"; exit 1; fi
g++  -g -O2 -I -L   -o dstest -L../../drawstuff/src dstest-dstest.o -ldrawstuff   -lGL -lGLU -lXmu -lXi -lX11  -lstdc++ -lm -lpthread  -lstdc++ -lm -lpthread
make[2]: Leaving directory `/home/sudarshan/Gazebo Help/ode-0.8/drawstuff/dstest'
make[2]: Entering directory `/home/sudarshan/Gazebo Help/ode-0.8/drawstuff'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/sudarshan/Gazebo Help/ode-0.8/drawstuff'
make[1]: Leaving directory `/home/sudarshan/Gazebo Help/ode-0.8/drawstuff'
Making all in ode
make[1]: Entering directory `/home/sudarshan/Gazebo Help/ode-0.8/ode'
Making all in src
make[2]: Entering directory `/home/sudarshan/Gazebo Help/ode-0.8/ode/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I../../include/ode  -O2 -fPIC  -I../../include -I../../include  -I/home/sudarshan/Gazebo Help/ode-0.8/OPCODE -I/home/sudarshan/Gazebo Help/ode-0.8/OPCODE/Ice -DdTRIMESH_ENABLED -DdTRIMESH_OPCODE -g -O2 -I -L -MT libode_a-obstack.o -MD -MP -MF ".deps/libode_a-obstack.Tpo" -c -o libode_a-obstack.o `test -f 'obstack.cpp' || echo './'`obstack.cpp; \
        then mv -f ".deps/libode_a-obstack.Tpo" ".deps/libode_a-obstack.Po"; else rm -f ".deps/libode_a-obstack.Tpo"; exit 1; fi
g++: Help/ode-0.8/OPCODE: No such file or directory
g++: Help/ode-0.8/OPCODE/Ice: No such file or directory
make[2]: *** [libode_a-obstack.o] Error 1
make[2]: Leaving directory `/home/sudarshan/Gazebo Help/ode-0.8/ode/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sudarshan/Gazebo Help/ode-0.8/ode'
make: *** [all-recursive] Error 1

Could you please tell me what is wrong and how I can correct this? I have one more question. The configure output says that it will install all the stuff in /usr/local/bin. Now I have a lot of programs that are installed in /usr/bin. What is the difference between installing in these two folders?


Thanks.

---

### Post by Enselic on 2007-07-22
Regarding your second question:

Linux software are installed in so called prefix. Typical prefixes are /usr and /usr/local.

The prefix simply denots where files are to be installed. Libraries typically go into $PREFIX/lib and binaries into $PREFIX/bin.

"your own" software is typcally placed in the /usr/local prefix to avoid conflicts with programs provided by the distro, which are typically instlled in the /usr prefix.

---

### Post by testube_babies on 2007-07-22
Try renaming the Gazebo Help folder to Gazebo_Help.  Sometimes compilers have problems parsing characters that need an escape sequence, such as the space.

I'm not sure this will work, though, since it seems some of it compiled fine, and g++ usually doesn't run into this problem.

---

### Post by linuxnovice on 2007-07-22
Hi,
That worked! ODE installed after I changed the dir name from Gazebo Help to just Gazebo. I then went on to  compile and install Gazebo itself and player, stage (for which there were .deb files). Anyway, when I attempted to start gazebo by just typing gazebo into konsole I got the following error:

gazebo: error while loading shared libraries: libode.so: cannot open shared object file: No such file or directory

This is weired because I thought that once I install ode libode should have installed....I also made sure that both the programs got installed in /usr/local.

Any ideas?
Thanks.

---

### Post by geraldm on 2007-07-23
in Linux, after installing the libraries, you must also do one:
!) reboot
2) (as root execute) ldconfig

Linux works out of a cache; one of the above flushes/renews the cache.

Gerald

---

### Post by bodhi.zazen on 2007-07-23
Off topic : You might want to consider checkinstall

A caution, checkinstall does not always work ,,,

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

	[http://www.howtoforge.com/howto_linux_debian_deb_checkinstall](http://www.howtoforge.com/howto_linux_debian_deb_checkinstall)

---

### Post by linuxnovice on 2007-07-23
Hi,
I rebooted and tried but it still gives the same error. I did use checkinstall for installing all these....

---

