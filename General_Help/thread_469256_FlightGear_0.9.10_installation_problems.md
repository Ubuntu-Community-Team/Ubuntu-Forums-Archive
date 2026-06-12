---
title: "FlightGear 0.9.10 installation problems"
date: 2007-06-09
forum: General Help
---

### Post by cmillican on 2007-06-09
I downloaded the .tar.gz of FlightGear, but, after running ./configure and getting all necessary dependancies, I typed "make", and got this:

```
$ make
Making all in tests
make[1]: Entering directory `/tmp/FlightGear-0.9.10/tests'
if gcc -DHAVE_CONFIG_H -I. -I. -I../src/Include   -I/usr/local/include  -g -O2 -D_REENTRANT -MT al-info.o -MD -MP -MF ".deps/al-info.Tpo" -c -o al-info.o al-info.c; \
        then mv -f ".deps/al-info.Tpo" ".deps/al-info.Po"; else rm -f ".deps/al-info.Tpo"; exit 1; fi
al-info.c:8:20: error: AL/al.h: No such file or directory
al-info.c:9:21: error: AL/alc.h: No such file or directory
al-info.c:11:24: error: AL/alext.h: No such file or directory
al-info.c:20:26: error: AL/altypes.h: No such file or directory
al-info.c:21:27: error: AL/alctypes.h: No such file or directory
al-info.c: In function ‘main’:
al-info.c:29: error: ‘ALCint’ undeclared (first use in this function)
al-info.c:29: error: (Each undeclared identifier is reported only once
al-info.c:29: error: for each function it appears in.)
al-info.c:29: error: expected ‘;’ before ‘i’
al-info.c:30: error: expected ‘;’ before ‘data’
al-info.c:31: error: ‘ALCdevice’ undeclared (first use in this function)
al-info.c:31: error: ‘device’ undeclared (first use in this function)
al-info.c:32: error: ‘ALCcontext’ undeclared (first use in this function)
al-info.c:32: error: ‘context’ undeclared (first use in this function)
al-info.c:34: error: ‘ALCenum’ undeclared (first use in this function)
al-info.c:34: error: expected ‘;’ before ‘error’
al-info.c:50: error: ‘AL_VENDOR’ undeclared (first use in this function)
al-info.c:50: warning: assignment makes pointer from integer without a cast
al-info.c:53: error: ‘AL_RENDERER’ undeclared (first use in this function)
al-info.c:53: warning: assignment makes pointer from integer without a cast
al-info.c:56: error: ‘AL_VERSION’ undeclared (first use in this function)
al-info.c:56: warning: assignment makes pointer from integer without a cast
al-info.c:59: error: ‘AL_EXTENSIONS’ undeclared (first use in this function)
al-info.c:59: warning: assignment makes pointer from integer without a cast
al-info.c:65: error: ‘AL_TRUE’ undeclared (first use in this function)
al-info.c:67: error: ‘ALC_DEVICE_SPECIFIER’ undeclared (first use in this function)
al-info.c:67: warning: assignment makes pointer from integer without a cast
al-info.c:71: error: ‘ALC_MAJOR_VERSION’ undeclared (first use in this function)
al-info.c:71: error: ‘data’ undeclared (first use in this function)
al-info.c:73: error: ‘ALC_MINOR_VERSION’ undeclared (first use in this function)
al-info.c:76: error: ‘ALC_EXTENSIONS’ undeclared (first use in this function)
al-info.c:76: warning: assignment makes pointer from integer without a cast
al-info.c:79: error: ‘error’ undeclared (first use in this function)
al-info.c:85: error: ‘ALC_DEFAULT_DEVICE_SPECIFIER’ undeclared (first use in this function)
al-info.c:85: warning: assignment makes pointer from integer without a cast
make[1]: *** [al-info.o] Error 1
make[1]: Leaving directory `/tmp/FlightGear-0.9.10/tests'
make: *** [all-recursive] Error 1
```

Any help is greatly appreciated.

Chris

---

### Post by Sslaxx on 2007-06-09
Looks like you're missing the OpenAL libraries? Try installing the libopenal-dev package.

---

### Post by cmillican on 2007-06-09
Ok, I installed that, but now I just get different errors:

```
$ make
Making all in tests
make[1]: Entering directory `/tmp/FlightGear-0.9.10/tests'
gcc  -g -O2 -D_REENTRANT  -L/usr/X11R6/lib -L/usr/local/lib -o al-info  al-info.o -lopenal -ldl -lm   -lpthread  
if g++ -DHAVE_CONFIG_H -I. -I. -I../src/Include   -I/usr/local/include  -g -O2 -D_REENTRANT -MT test-gethostname.o -MD -MP -MF ".deps/test-gethostname.Tpo" -c -o test-gethostname.o test-gethostname.cxx; \
        then mv -f ".deps/test-gethostname.Tpo" ".deps/test-gethostname.Po"; else rm -f ".deps/test-gethostname.Tpo"; exit 1; fi
g++  -g -O2 -D_REENTRANT  -L/usr/X11R6/lib -L/usr/local/lib -o test-gethostname  test-gethostname.o  
if g++ -DHAVE_CONFIG_H -I. -I. -I../src/Include   -I/usr/local/include  -g -O2 -D_REENTRANT -MT test-mktime.o -MD -MP -MF ".deps/test-mktime.Tpo" -c -o test-mktime.o test-mktime.cxx; \
        then mv -f ".deps/test-mktime.Tpo" ".deps/test-mktime.Po"; else rm -f ".deps/test-mktime.Tpo"; exit 1; fi
g++  -g -O2 -D_REENTRANT  -L/usr/X11R6/lib -L/usr/local/lib -o test-mktime  test-mktime.o  
if g++ -DHAVE_CONFIG_H -I. -I. -I../src/Include   -I/usr/local/include  -g -O2 -D_REENTRANT -MT test-text.o -MD -MP -MF ".deps/test-text.Tpo" -c -o test-text.o test-text.cxx; \
        then mv -f ".deps/test-text.Tpo" ".deps/test-text.Po"; else rm -f ".deps/test-text.Tpo"; exit 1; fi
g++  -g -O2 -D_REENTRANT  -L/usr/X11R6/lib -L/usr/local/lib -o test-text  test-text.o  
if g++ -DHAVE_CONFIG_H -I. -I. -I../src/Include   -I/usr/local/include  -g -O2 -D_REENTRANT -MT test-up.o -MD -MP -MF ".deps/test-up.Tpo" -c -o test-up.o test-up.cxx; \
        then mv -f ".deps/test-up.Tpo" ".deps/test-up.Po"; else rm -f ".deps/test-up.Tpo"; exit 1; fi
g++  -g -O2 -D_REENTRANT  -L/usr/X11R6/lib -L/usr/local/lib -o test-up  test-up.o -lsgmath -lsgxml -lsgmisc -lsgdebug -lsgstructure -lsgtiming -lplibsg -lplibul -lz -ldl -lm  
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libsgmisc.so: undefined reference to `SGPropertyNode::getDoubleValue() const'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libsgmisc.so: undefined reference to `SGPropertyNode::setDoubleValue(double)'
collect2: ld returned 1 exit status
make[1]: *** [test-up] Error 1
make[1]: Leaving directory `/tmp/FlightGear-0.9.10/tests'
make: *** [all-recursive] Error 1
```

Thanks,

Chris

---

### Post by Sslaxx on 2007-06-10
FlightGear has a fair few dependencies. Try installing simgear-dev. Also, check the README and INSTALL files to see if you can find out what other packages you might need to install.

---

### Post by ramjet_1953 on 2007-06-10
Why are you trying to install this by compiling?

FlightGear 0.9.10 is available for install, using Synaptic Package Manager.

Just make sure that you have enabled the extra repositories in Synaptic and do a search for [COLOR="Blue"]flightgear[/COLOR] .

Regards,
Roger :cool:

---

### Post by cesarespcab on 2008-06-19
> **cmillican said:**
> Ok, I installed that, but now I just get different errors:

```
$ make
Making all in tests
make[1]: Entering directory `/tmp/FlightGear-0.9.10/tests'
gcc  -g -O2 -D_REENTRANT  -L/usr/X11R6/lib -L/usr/local/lib -o al-info  al-info.o -lopenal -ldl -lm   -lpthread  
if g++ -DHAVE_CONFIG_H -I. -I. -I../src/Include   -I/usr/local/include  -g -O2 -D_REENTRANT -MT test-gethostname.o -MD -MP -MF ".deps/test-gethostname.Tpo" -c -o test-gethostname.o test-gethostname.cxx; \
        then mv -f ".deps/test-gethostname.Tpo" ".deps/test-gethostname.Po"; else rm -f ".deps/test-gethostname.Tpo"; exit 1; fi
g++  -g -O2 -D_REENTRANT  -L/usr/X11R6/lib -L/usr/local/lib -o test-gethostname  test-gethostname.o  
if g++ -DHAVE_CONFIG_H -I. -I. -I../src/Include   -I/usr/local/include  -g -O2 -D_REENTRANT -MT test-mktime.o -MD -MP -MF ".deps/test-mktime.Tpo" -c -o test-mktime.o test-mktime.cxx; \
        then mv -f ".deps/test-mktime.Tpo" ".deps/test-mktime.Po"; else rm -f ".deps/test-mktime.Tpo"; exit 1; fi
g++  -g -O2 -D_REENTRANT  -L/usr/X11R6/lib -L/usr/local/lib -o test-mktime  test-mktime.o  
if g++ -DHAVE_CONFIG_H -I. -I. -I../src/Include   -I/usr/local/include  -g -O2 -D_REENTRANT -MT test-text.o -MD -MP -MF ".deps/test-text.Tpo" -c -o test-text.o test-text.cxx; \
        then mv -f ".deps/test-text.Tpo" ".deps/test-text.Po"; else rm -f ".deps/test-text.Tpo"; exit 1; fi
g++  -g -O2 -D_REENTRANT  -L/usr/X11R6/lib -L/usr/local/lib -o test-text  test-text.o  
if g++ -DHAVE_CONFIG_H -I. -I. -I../src/Include   -I/usr/local/include  -g -O2 -D_REENTRANT -MT test-up.o -MD -MP -MF ".deps/test-up.Tpo" -c -o test-up.o test-up.cxx; \
        then mv -f ".deps/test-up.Tpo" ".deps/test-up.Po"; else rm -f ".deps/test-up.Tpo"; exit 1; fi
g++  -g -O2 -D_REENTRANT  -L/usr/X11R6/lib -L/usr/local/lib -o test-up  test-up.o -lsgmath -lsgxml -lsgmisc -lsgdebug -lsgstructure -lsgtiming -lplibsg -lplibul -lz -ldl -lm  
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libsgmisc.so: undefined reference to `SGPropertyNode::getDoubleValue() const'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libsgmisc.so: undefined reference to `SGPropertyNode::setDoubleValue(double)'
collect2: ld returned 1 exit status
make[1]: *** [test-up] Error 1
make[1]: Leaving directory `/tmp/FlightGear-0.9.10/tests'
make: *** [all-recursive] Error 1
```

Thanks,

Chris


hello. i'm using ubuntu 8.04, and i installed all dependencies for flightgear-1.0 including "simgear-dev" from synaptics. Then when i compiled the flightgear code, i got exactly the same error.

Solution: download simgear-1.0.0 code from [http://www.simgear.org/downloads.html](http://www.simgear.org/downloads.html), compile it and install it. (autogen, configure, make, sudo make install)

Ready: I compiled FlightGear again and everything was ok, i'm now fliying :)

I hope it helps


(excuse my writing, I'm practicing)

--------------------------------------------------------------
"pack your six senses, come to Peru, land of the Incas"
[http://www.peru.info/perueng.asp](http://www.peru.info/perueng.asp)
--------------------------------------------------------------

---

