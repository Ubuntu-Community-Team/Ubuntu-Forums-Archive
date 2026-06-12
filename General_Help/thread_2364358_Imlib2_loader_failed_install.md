---
title: "Imlib2_loader failed install"
date: 2017-06-22
forum: General Help
---

### Post by zerobytez on 2017-06-22
I'm trying to install PyPanel, and I've been having trouble at every corner, but this is the only error I'm having I can't seem to fix:

```
####@####-K50IE:~/Desktop/imlib2_loaders-1.4.10$ sudo make install
Making install in src
make[1]: Entering directory '/home/####/Desktop/imlib2_loaders-1.4.10/src'
Making install in modules
make[2]: Entering directory '/home/####/Desktop/imlib2_loaders-1.4.10/src/modules'
Making install in loaders
make[3]: Entering directory '/home/####/Desktop/imlib2_loaders-1.4.10/src/modules/loaders'
  CC       xcf_la-loader_xcf.lo
loader_xcf.c:58:22: fatal error: X11/Xlib.h: No such file or directory
 #include <X11/Xlib.h>
                                                        ^
compilation terminated.
Makefile:511: recipe for target 'xcf_la-loader_xcf.lo' failed
make[3]: *** [xcf_la-loader_xcf.lo] Error 1
make[3]: Leaving directory '/home/####/Desktop/imlib2_loaders-1.4.10/src/modules/loaders'
Makefile:353: recipe for target 'install-recursive' failed
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory '/home/####/Desktop/imlib2_loaders-1.4.10/src/modules'
Makefile:353: recipe for target 'install-recursive' failed
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory '/home/####/Desktop/imlib2_loaders-1.4.10/src'
Makefile:414: recipe for target 'install-recursive' failed
make: *** [install-recursive] Error 1
```

I have Xlib installed, so I have no idea what the error actually is, I'm admittedly not a Linux genius :/

---

### Post by slickymaster on 2017-06-22
*Thread moved to **General Help**.*

---

### Post by steeldriver on 2017-06-22
Do you have **libx11-dev** installed? That's the package that provides the X11/Xlib.h header file:

```

$ dpkg -S /usr/include/X11/Xlib.h
libx11-dev:amd64: /usr/include/X11/Xlib.h

```

---

### Post by zerobytez on 2017-06-22
It says no, but I know I installed it... how would one install it, just to check I'm not doing something stupid?

---

### Post by steeldriver on 2017-06-22
If you installed libx11 outside of the apt/dpk system (from source, for example) and the header is somewhere other than /usr/include, then you will need to tell the compiler where to find it - the best way to do that will depend on the build system (autoconf / cmake or whatever - or plain Makefile) - for example passing "CFLAGS=-I/usr/local/include/X11"

If you HAVEN'T installed it outside of apt/dpkg, and want to install the packaged version from the repository, you can use Software Center, or 

```

sudo apt install libx11-dev

```

If it's already installed, apt will tell you.

---

### Post by zerobytez on 2017-06-22
> **steeldriver said:**
> If you installed libx11 outside of the apt/dpk system (from source, for example) and the header is somewhere other than /usr/include, then you will need to tell the compiler where to find it - the best way to do that will depend on the build system (autoconf / cmake or whatever - or plain Makefile) - for example passing "CFLAGS=-I/usr/local/include/X11"

If you HAVEN'T installed it outside of apt/dpkg, and want to install the packaged version from the repository, you can use Software Center, or 

```

sudo apt install libx11-dev

```

If it's already installed, apt will tell you.

Ok, it's installed, now throwing a new error:

```

####@####-K50IE:~/Desktop/imlib2_loaders-1.4.10$ sudo make install
Making install in src
make[1]: Entering directory '/home/####/Desktop/imlib2_loaders-1.4.10/src'
Making install in modules
make[2]: Entering directory '/home/####/Desktop/imlib2_loaders-1.4.10/src/modules'
Making install in loaders
make[3]: Entering directory '/home/nathan/Desktop/imlib2_loaders-1.4.10/src/modules/loaders'
  CC       xcf_la-loader_xcf.lo
  CC       xcf_la-loader_xcf_pixelfuncs.lo
  CCLD     xcf.la
  CC       ico_la-loader_ico.lo
loader_ico.c:33:33: fatal error: X11/extensions/XShm.h: No such file or directory
 #include <X11/extensions/XShm.h>
                                 ^
compilation terminated.
Makefile:504: recipe for target 'ico_la-loader_ico.lo' failed
make[3]: *** [ico_la-loader_ico.lo] Error 1
make[3]: Leaving directory '/home/na####than/Desktop/imlib2_loaders-1.4.10/src/modules/loaders'
Makefile:353: recipe for target 'install-recursive' failed
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory '/home/####/Desktop/imlib2_loaders-1.4.10/src/modules'
Makefile:353: recipe for target 'install-recursive' failed
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory '/home/####/Desktop/imlib2_loaders-1.4.10/src'
Makefile:414: recipe for target 'install-recursive' failed
make: *** [install-recursive] Error 1


```

---

### Post by steeldriver on 2017-06-22
That would be provided by **libxext-dev** I believe

If you're not short of disk space, it will probably make sense to install the **xorg-dev** metapackage rather than picking off the dependencies one-by-one

---

### Post by zerobytez on 2017-06-23
The internet failed me :/
Imlib2's been installed, but PyPanel can't find it, simply saying it requires it.

---

### Post by zerobytez on 2017-06-23
Hang on, I figured out the error. Al good to go, thanks.

---

