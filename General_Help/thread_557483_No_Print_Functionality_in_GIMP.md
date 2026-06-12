---
title: "No Print Functionality in GIMP??"
date: 2007-09-22
forum: General Help
---

### Post by ctsdownloads on 2007-09-22
gimp-print is installed, along with every lib I can find relating to printing - nothing off of the File menu is showing up relating to printing. Check available plugins - no mention of printing, surely I am not losing my mind here - this renders GIMP to half its potential value without this funcionality.

Using 2.2.11 GIMP]

---

### Post by Maestro23 on 2007-09-22
Do you have gutenprint installed?

[http://gutenprint.sourceforge.net/index.php3](http://gutenprint.sourceforge.net/index.php3)

---

### Post by ctsdownloads on 2007-09-22
Hmm, should be on my system already, but it does not appear to be. Which version would have normally come with Edgy? Any idea? I say this as compiling and then chasing dependencies myself is not exactly what I had in mind. A Deb package would be great. :)

---

### Post by ctsdownloads on 2007-09-22
Compiling...always fun...

> ake[2]: Leaving directory `/home/matt/Desktop/gutenprint-5.1.3/src'
Making all in samples
make[2]: Entering directory `/home/matt/Desktop/gutenprint-5.1.3/samples'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/matt/Desktop/gutenprint-5.1.3/samples'
Making all in test
make[2]: Entering directory `/home/matt/Desktop/gutenprint-5.1.3/test'
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -I../include -I../include -I../src/main  -Wall -Wcast-align -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Wwrite-strings -Werror-implicit-function-declaration -Winline -Wformat=2 -finline-limit=1048576   -Disfinite=finite  -O6 -MT testdither.o -MD -MP -MF ".deps/testdither.Tpo" -c -o testdither.o testdither.c; \
        then mv -f ".deps/testdither.Tpo" ".deps/testdither.Po"; else rm -f ".deps/testdither.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc  -Disfinite=finite  -O6   -o testdither  testdither.o ../src/main/libgutenprint.la  
mkdir .libs
gcc -Disfinite=finite -O6 -o .libs/testdither testdither.o  ../src/main/.libs/libgutenprint.so -lm -Wl,--rpath -Wl,/usr/local/lib
creating testdither
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -I../include -I../include -I../src/main  -Wall -Wcast-align -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Wwrite-strings -Werror-implicit-function-declaration -Winline -Wformat=2 -finline-limit=1048576   -Disfinite=finite  -O6 -MT escp2-weavetest.o -MD -MP -MF ".deps/escp2-weavetest.Tpo" -c -o escp2-weavetest.o escp2-weavetest.c; \
        then mv -f ".deps/escp2-weavetest.Tpo" ".deps/escp2-weavetest.Po"; else rm -f ".deps/escp2-weavetest.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc  -Disfinite=finite  -O6   -o escp2-weavetest  escp2-weavetest.o ../src/main/libgutenprint.la  
gcc -Disfinite=finite -O6 -o .libs/escp2-weavetest escp2-weavetest.o  ../src/main/.libs/libgutenprint.so -lm -Wl,--rpath -Wl,/usr/local/lib
creating escp2-weavetest
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -I../include -I../include -I../src/main  -Wall -Wcast-align -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Wwrite-strings -Werror-implicit-function-declaration -Winline -Wformat=2 -finline-limit=1048576   -Disfinite=finite  -O6 -MT unprint.o -MD -MP -MF ".deps/unprint.Tpo" -c -o unprint.o unprint.c; \
        then mv -f ".deps/unprint.Tpo" ".deps/unprint.Po"; else rm -f ".deps/unprint.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc  -Disfinite=finite  -O6   -o unprint  unprint.o ../src/main/libgutenprint.la  
gcc -Disfinite=finite -O6 -o .libs/unprint unprint.o  ../src/main/.libs/libgutenprint.so -lm -Wl,--rpath -Wl,/usr/local/lib
creating unprint
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -I../include -I../include -I../src/main  -Wall -Wcast-align -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Wwrite-strings -Werror-implicit-function-declaration -Winline -Wformat=2 -finline-limit=1048576   -Disfinite=finite  -O6 -MT pcl-unprint.o -MD -MP -MF ".deps/pcl-unprint.Tpo" -c -o pcl-unprint.o pcl-unprint.c; \
        then mv -f ".deps/pcl-unprint.Tpo" ".deps/pcl-unprint.Po"; else rm -f ".deps/pcl-unprint.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc  -Disfinite=finite  -O6   -o pcl-unprint  pcl-unprint.o ../src/main/libgutenprint.la  
gcc -Disfinite=finite -O6 -o .libs/pcl-unprint pcl-unprint.o  ../src/main/.libs/libgutenprint.so -lm -Wl,--rpath -Wl,/usr/local/lib
creating pcl-unprint
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -I../include -I../include -I../src/main  -Wall -Wcast-align -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Wwrite-strings -Werror-implicit-function-declaration -Winline -Wformat=2 -finline-limit=1048576   -Disfinite=finite  -O6 -MT bjc-unprint.o -MD -MP -MF ".deps/bjc-unprint.Tpo" -c -o bjc-unprint.o bjc-unprint.c; \
        then mv -f ".deps/bjc-unprint.Tpo" ".deps/bjc-unprint.Po"; else rm -f ".deps/bjc-unprint.Tpo"; exit 1; fi
bjc-unprint.c: In function ‘main’:
bjc-unprint.c:457: warning: ‘ymax’ may be used uninitialized in this function
bjc-unprint.c:457: warning: ‘ymin’ may be used uninitialized in this function
bjc-unprint.c:456: warning: ‘xmax’ may be used uninitialized in this function
bjc-unprint.c:456: warning: ‘xmin’ may be used uninitialized in this function
/bin/sh ../libtool --tag=CC --mode=link gcc  -Disfinite=finite  -O6   -o bjc-unprint  bjc-unprint.o ../src/main/libgutenprint.la  
gcc -Disfinite=finite -O6 -o .libs/bjc-unprint bjc-unprint.o  ../src/main/.libs/libgutenprint.so -lm -Wl,--rpath -Wl,/usr/local/lib
creating bjc-unprint
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -I../include -I../include -I../src/main  -Wall -Wcast-align -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Wwrite-strings -Werror-implicit-function-declaration -Winline -Wformat=2 -finline-limit=1048576   -Disfinite=finite  -O6 -MT curve.o -MD -MP -MF ".deps/curve.Tpo" -c -o curve.o curve.c; \
        then mv -f ".deps/curve.Tpo" ".deps/curve.Po"; else rm -f ".deps/curve.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc  -Disfinite=finite  -O6   -o curve  curve.o ../src/main/libgutenprint.la  
gcc -Disfinite=finite -O6 -o .libs/curve curve.o  ../src/main/.libs/libgutenprint.so -lm -Wl,--rpath -Wl,/usr/local/lib
creating curve
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -I../include -I../include -I../src/main  -Wall -Wcast-align -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Wwrite-strings -Werror-implicit-function-declaration -Winline -Wformat=2 -finline-limit=1048576   -Disfinite=finite  -O6 -MT xml-curve.o -MD -MP -MF ".deps/xml-curve.Tpo" -c -o xml-curve.o xml-curve.c; \
        then mv -f ".deps/xml-curve.Tpo" ".deps/xml-curve.Po"; else rm -f ".deps/xml-curve.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc  -Disfinite=finite  -O6   -o xml-curve  xml-curve.o ../src/main/libgutenprint.la  
gcc -Disfinite=finite -O6 -o .libs/xml-curve xml-curve.o  ../src/main/.libs/libgutenprint.so -lm -Wl,--rpath -Wl,/usr/local/lib
creating xml-curve
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -I../include -I../include -I../src/main  -Wall -Wcast-align -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Wwrite-strings -Werror-implicit-function-declaration -Winline -Wformat=2 -finline-limit=1048576   -Disfinite=finite  -O6 -MT pixma_parse.o -MD -MP -MF ".deps/pixma_parse.Tpo" -c -o pixma_parse.o pixma_parse.c; \
        then mv -f ".deps/pixma_parse.Tpo" ".deps/pixma_parse.Po"; else rm -f ".deps/pixma_parse.Tpo"; exit 1; fi
pixma_parse.c: In function ‘main’:
pixma_parse.h:158: warning: inlining failed in call to ‘get_bits’: --param large-function-growth limit reached
pixma_parse.c:245: warning: called from here
/bin/sh ../libtool --tag=CC --mode=link gcc  -Disfinite=finite  -O6   -o pixma_parse  pixma_parse.o   
gcc -Disfinite=finite -O6 -o pixma_parse pixma_parse.o 
make[2]: Leaving directory `/home/matt/Desktop/gutenprint-5.1.3/test'
Making all in po
make[2]: Entering directory `/home/matt/Desktop/gutenprint-5.1.3/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/matt/Desktop/gutenprint-5.1.3/po'
Making all in man
make[2]: Entering directory `/home/matt/Desktop/gutenprint-5.1.3/man'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/matt/Desktop/gutenprint-5.1.3/man'
Making all in doc
make[2]: Entering directory `/home/matt/Desktop/gutenprint-5.1.3/doc'
Making all in developer
make[3]: Entering directory `/home/matt/Desktop/gutenprint-5.1.3/doc/developer'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/matt/Desktop/gutenprint-5.1.3/doc/developer'
make[3]: Entering directory `/home/matt/Desktop/gutenprint-5.1.3/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/matt/Desktop/gutenprint-5.1.3/doc'
make[2]: Leaving directory `/home/matt/Desktop/gutenprint-5.1.3/doc'
Making all in scripts
make[2]: Entering directory `/home/matt/Desktop/gutenprint-5.1.3/scripts'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/matt/Desktop/gutenprint-5.1.3/scripts'
make[2]: Entering directory `/home/matt/Desktop/gutenprint-5.1.3'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/matt/Desktop/gutenprint-5.1.3'
make[1]: Leaving directory `/home/matt/Desktop/gutenprint-5.1.3'
matt@matt-desktop:~/Desktop/gutenprint-5.1.3$ make install
Making install in include
make[1]: Entering directory `/home/matt/Desktop/gutenprint-5.1.3/include'
Making install in gutenprint
make[2]: Entering directory `/home/matt/Desktop/gutenprint-5.1.3/include/gutenprint'
make[3]: Entering directory `/home/matt/Desktop/gutenprint-5.1.3/include/gutenprint'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/gutenprint" || mkdir -p -- "/usr/local/include/gutenprint"
mkdir: cannot create directory `/usr/local/include/gutenprint': Permission denied
make[3]: *** [install-nodist_pkgincludeHEADERS] Error 1
make[3]: Leaving directory `/home/matt/Desktop/gutenprint-5.1.3/include/gutenprint'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/matt/Desktop/gutenprint-5.1.3/include/gutenprint'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/matt/Desktop/gutenprint-5.1.3/include'
make: *** [install-recursive] Error 1


Yeah, really need to skip that and just let a Deb package do the heavy lifting here.

---

### Post by ctsdownloads on 2007-09-22
Unless someone has a Deb package that works, I am may be forced to drop GIMP for Photoshop through WINE - this is pretty silly really, it's common enough that a working Deb package for Edgy should exist somewhere.

---

### Post by ctsdownloads on 2007-09-22
Also tried > [http://security.ubuntu.com/ubuntu/pool/main/g/gutenprint/gimp-print_5.0.0-2ubuntu2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gutenprint/gimp-print_5.0.0-2ubuntu2_i386.deb)

Still not giving me the option and I would think that Gluten-print would have been included in that package?? Why is this not include by default? It's soooo obvious that printing funtionality is part of a Photoshop clone like GIMP? :confused:

---

### Post by Steveway on 2007-09-22
Why are you running edgy?
It's not a LTS release and Feisty has been out for a loooong time now.
Gutsy will be there in a month.
You should upgrade to a newer release with a newer version of Gimp, that should fix your issues.
EDIT: And stop bumping every minute, just edit your posts!

---

### Post by Maestro23 on 2007-09-22
Do you have "build-essential" installed?

> sudo apt-get install build-essential

---

### Post by ctsdownloads on 2007-09-22
**Maestro23:** Here it is-
build-essential is already the newest version.


**Steveway:** Was not at all impressed with the headaches given to me with Feisty, despite what others may believe. The new networking scheme nearly made me drop Ubuntu - very disappointing considering that it was totally unneeded in MHO. Zeroconf indeed...

Most important to me was the issues with SANE and my Cannon scanner - thanks, but no thanks. Edgy is solid enough for another month or so, and Feisty is good enough on my notebook for now.

Will be looking at Gutsy here sooner or later - but will be doing a clean install as there are entire threads about the nightmare that can come with the upgrade option. ;)

That's unfortunate about the print option, will try it on my Feisty notebook and see if this has been resolved on that release. If not, well, that's life I guess. I really hate to have to use Photoshop because such an obvious bug goes unchanged. Again, will check this in Feisty.

---

