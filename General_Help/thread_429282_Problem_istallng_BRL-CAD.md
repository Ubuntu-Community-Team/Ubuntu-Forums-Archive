---
title: "Problem istallng BRL-CAD"
date: 2007-05-01
forum: General Help
---

### Post by Ag_Smith on 2007-05-01
I try to making brl-cad 7.10 in ubuntu:

gioacchino@server:~/Desktop/brlcad-7.10.0$ ./configure --enable-optimized --enable-dependency-tracking --enable-debug --enable-adrt-build --with-x11 --with-opengl --with-python
.
.
.
.
.
.
Done.

BRL-CAD Release 7.10.0, Build 20070501

             Prefix: /usr/brlcad
           Binaries: /usr/brlcad/bin
Configuration files: /usr/brlcad/etc
       Manual pages: /usr/brlcad/man

CC       = gcc
CXX      = g++
CFLAGS   =   -pipe -fno-strict-aliasing -fno-common -fexceptions -g -O3
CXXFLAGS =   -pipe -fno-strict-aliasing -fno-common -fexceptions -g -O3
CPPFLAGS = -I/usr/local/include -DBRLCADBUILD=1 -I$(top_srcdir)/include
LDFLAGS  = -L/usr/local/lib -pipe -fno-strict-aliasing -fno-common -fexceptions -g -O3
LIBS     =

Build Tcl ............................: yes
Build Tk .............................: yes
Build Itcl/Itk .......................: yes
Build IWidgets .......................: yes
Build BLT ............................: yes
Build tkImg ..........................: yes
Build libpng .........................: yes
Build libregex .......................: no (using system)
Build zlib ...........................: no (using system)
Build termlib ........................: no (using system)
Build Utah Raster Toolkit.............: yes
Build openNURBS.......................: yes
Build jove ...........................: yes

ADRT support .........................: yes
X11 support ..........................: yes
OpenGL support .......................: yes
Java Developer Kit support ...........: no
Enable run-time debugging ............: yes

Build 64-bit release .................: no (32-bit)
Build optimized release ..............: yes
Build debug release ..................: yes
Build profile release ................: no
Build static libraries ...............: yes
Build shared/dynamic libraries .......: yes
Print verbose compilation warnings ...: no
Print verbose compilation progress ...: no

Only build benchmark suite ...........: no
Only build librtserver ...............: no
Install example geometry models ......: yes

Elapsed configuration time ...........: 20 seconds
---
./configure complete, type 'make' to begin building

gioacchino@server:~/Desktop/brlcad-7.10.0$ make 
.
.
.
.
.
.
.
.
.
.
.
.
Making all in fbserv
make[2]: Entering directory `/home/gioacchino/Desktop/brlcad-7.10.0/src/fbserv'
/bin/bash ../../libtool --silent --mode=link gcc  -pipe -fno-strict-aliasing -fno-common -fexceptions -g -O3  -L/usr/local/lib -pipe -fno-strict-aliasing -fno-common -fexceptions -g -O3 -o fbserv  fbserv.o server.o ../../src/libfb/libfb.la ../../src/libbu/libbu.la ../../src/libpkg/libpkg.la -L../../src/other/tcl/unix -ltcl8.5 -ldl -lm -Lyes/lib -lX11 -lXi -lXext -lX11 -lGL ../../src/libbu/libbu.la -L../../src/other/tcl/unix -ltcl8.5 -ldl -lm -lm -lc -lpthread ../../src/libpkg/libpkg.la
../../libtool: line 1323: cd: yes/lib: No such file or directory
libtool: link: cannot determine absolute directory name of `yes/lib'
make[2]: *** [fbserv] Error 1
make[2]: Leaving directory `/home/gioacchino/Desktop/brlcad-7.10.0/src/fbserv'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gioacchino/Desktop/brlcad-7.10.0/src'
make: *** [all-recursive] Error 1



how to fix this ????

I have already fix before making this error with jove-tutorial:
> 
Making install in jove
make[3]: Entering directory `/home/gioacchino/Desktop/brlcad-7.10.0/src/other/jove'
make[3]: *** No rule to make target `jove-tutorial', needed by `all-am'. Stop.
make[3]: Leaving directory `/home/gioacchino/Desktop/brlcad-7.10.0/src/other/jove'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/gioacchino/Desktop/brlcad-7.10.0/src/other'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/gioacchino/Desktop/brlcad-7.10.0/src'
make: *** [install-recursive] Error 1


with this tutorial

>  Hi!

I got the same problem when compiling brl-cad from the source on my Ubuntu Dapper. Solution was to change 3 makefiles (Makefile, Makefile.am and Makefile.in) in directory ../brlcad-7.10.0/src/other/jove/.

Open these files with text editor and remove strings "jove-tutorial" and the "\" at the end of "describe.com".

Before changing:

desc_DATA = \
describe.com \
jove-tutorial

After changing:

desc_DATA = \
describe.com

Save files and then run make again. Compilation should continue without problems.

With best regards,

eerik


---

