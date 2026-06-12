---
title: "Making packages and conftest.c"
date: 2007-03-19
forum: General Help
---

### Post by tscook on 2007-03-19
Every package I attempt to
```
./configure
make
make install
```

returns:

```
tscook@tscook-laptop:~/Desktop/imlib2_loaders-1.3.0$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

So I check config.log, it doesn't help me much:

```
  	
configure:2401: checking for C compiler default output file name
configure:2428: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2431: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2470: error: C compiler cannot create executables
```

Trying to make and make install do not work since ./configure is apparently not working.

Googling conftest.c and confdefs.h and what they do/are and how I can fix this is also leaving me high and dry.

HALP

---

### Post by tscook on 2007-03-19
I realized I hadn't grabbed build_essentials but now I get this and it confuses me more:

```
make  all-recursive
make[1]: Entering directory `/home/tscook/Desktop/imlib2_loaders-1.3.0'
Making all in src
make[2]: Entering directory `/home/tscook/Desktop/imlib2_loaders-1.3.0/src'
Making all in modules
make[3]: Entering directory `/home/tscook/Desktop/imlib2_loaders-1.3.0/src/modules'
Making all in loaders
make[4]: Entering directory `/home/tscook/Desktop/imlib2_loaders-1.3.0/src/modules/loaders'
if /bin/bash ../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../.. -I. -I../../.. -I../../../src/modules/loaders     -g -O2 -MT loader_xcf.lo -MD -MP -MF ".deps/loader_xcf.Tpo" -c -o loader_xcf.lo loader_xcf.c; \
        then mv -f ".deps/loader_xcf.Tpo" ".deps/loader_xcf.Plo"; else rm -f ".deps/loader_xcf.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../.. -I. -I../../.. -I../../../src/modules/loaders -g -O2 -MT loader_xcf.lo -MD -MP -MF .deps/loader_xcf.Tpo -c loader_xcf.c  -fPIC -DPIC -o .libs/loader_xcf.o
loader_xcf.c:58:22: error: X11/Xlib.h: No such file or directory
In file included from loader_xcf.c:61:
image.h:85: error: expected specifier-qualifier-list before 'Pixmap'
image.h:134: error: expected declaration specifiers or '...' before 'Display'
image.h:134: error: expected declaration specifiers or '...' before 'Visual'
image.h:136: error: expected declaration specifiers or '...' before 'Colormap'
image.h:139: error: expected ')' before '*' token
image.h:159: error: expected ')' before '*' token
image.h:161: error: expected ')' before '*' token
make[4]: *** [loader_xcf.lo] Error 1
make[4]: Leaving directory `/home/tscook/Desktop/imlib2_loaders-1.3.0/src/modules/loaders'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/tscook/Desktop/imlib2_loaders-1.3.0/src/modules'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tscook/Desktop/imlib2_loaders-1.3.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tscook/Desktop/imlib2_loaders-1.3.0'
make: *** [all] Error 2

```

But Xlib is a part of XFree86 which is now X.org and I am now :confused:.

---

### Post by WW on 2007-03-19
Install the package **libx11-dev**.  It has the header files for compiling X programs.

---

