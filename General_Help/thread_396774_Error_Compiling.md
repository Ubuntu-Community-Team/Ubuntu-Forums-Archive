---
title: "Error Compiling"
date: 2007-03-29
forum: General Help
---

### Post by NeoReel on 2007-03-29
Hello all, 
 
First time poster, noob to Xubuntu...  I'm trying to compile an application and I need a bit of help if thats possible. 
 
I'm using xubuntu command line (no graphic interface) to compile Pixie with gcc 4.1.1. The source gets configured allright, but when I get to use "make", the compilation gets interrupted after a while because the process gets out of memory (g++). I compile on an Athlon 1.4ghz with 512mb of RAM. Do you have any ideas what I'm doing wrong ? 
 
Thanks in advance, 
 
M-A

---

### Post by smokey edgy on 2007-03-29
Could you show the ouput? Thanks.

---

### Post by NeoReel on 2007-03-29
Thanks for your fast reply.  I don't have access to the renderfarm computer at this time, so I will post it as soon as I get in tomorrow.  Sorry for the delay...

Regards,

---

### Post by NeoReel on 2007-03-30
Hello again,

  Here is the tail of the log when I compile :


##################################################

creating sdrc
make[3]: Leaving directory `/usr/local/src/Pixie/src/sdrc'
Making all in ri
make[3]: Entering directory `/usr/local/src/Pixie/src/ri'
if /bin/bash ../../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -Iutes.lo attributes.cpp; \
        then mv -f ".deps/attributes.Tpo" ".deps/attributes.Plo"; else rm -f ".d
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I.. -g -O2 -MT attributes.lo -MD -MP -MF .
if /bin/bash ../../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -Io brickmap.cpp; \
        then mv -f ".deps/brickmap.Tpo" ".deps/brickmap.Plo"; else rm -f ".deps/
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I.. -g -O2 -MT brickmap.lo -MD -MP -MF .de
if /bin/bash ../../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -Iundles.cpp; \
        then mv -f ".deps/bundles.Tpo" ".deps/bundles.Plo"; else rm -f ".deps/bu
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I.. -g -O2 -MT bundles.lo -MD -MP -MF .dep
if /bin/bash ../../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -Ipp; \
        then mv -f ".deps/cache.Tpo" ".deps/cache.Plo"; else rm -f ".deps/cache.
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I.. -g -O2 -MT cache.lo -MD -MP -MF .deps/
if /bin/bash ../../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -Ies.cpp; \
        then mv -f ".deps/curves.Tpo" ".deps/curves.Plo"; else rm -f ".deps/curv
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I.. -g -O2 -MT curves.lo -MD -MP -MF .deps
if /bin/bash ../../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I-c -o bsplinePatchgrid.lo bsplinePatchgrid.cpp; \
        then mv -f ".deps/bsplinePatchgrid.Tpo" ".deps/bsplinePatchgrid.Plo"; el
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I.. -g -O2 -MT bsplinePatchgrid.lo -MD -MPbsplinePatchgrid.o
if /bin/bash ../../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -Ipp; \
        then mv -f ".deps/debug.Tpo" ".deps/debug.Plo"; else rm -f ".deps/debug.
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I.. -g -O2 -MT debug.lo -MD -MP -MF .deps/
if /bin/bash ../../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -Ielayed.cpp; \
        then mv -f ".deps/delayed.Tpo" ".deps/delayed.Plo"; else rm -f ".deps/de
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I.. -g -O2 -MT delayed.lo -MD -MP -MF .dep
if /bin/bash ../../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -Io dlobject.cpp; \
        then mv -f ".deps/dlobject.Tpo" ".deps/dlobject.Plo"; else rm -f ".deps/
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I.. -g -O2 -MT dlobject.lo -MD -MP -MF .de
if /bin/bash ../../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -Ixecute.cpp; \
        then mv -f ".deps/execute.Tpo" ".deps/execute.Plo"; else rm -f ".deps/ex
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I.. -g -O2 -MT execute.lo -MD -MP -MF .dep
g++: Internal error: Killed (program cc1plus)
Please submit a full bug report.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.

make[3]: *** [execute.lo] Error 1
make[3]: Leaving directory `/usr/local/src/Pixie/src/ri'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/local/src/Pixie/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/Pixie'
make: *** [all] Error 2

################################


We are looking into inscreasing the swap space. Maybe that will fix the problem, but when I monitor the system ressources, I can clearly see the memory jumping from 30% usage to 94% usage.

Thanks for any feedback.

M-A

---

### Post by NeoReel on 2007-04-02
never mind, it was just a crazy ammount or RAM that was required to compile the program and my swap space was not set.

Thanks.

---

