---
title: "How can I installed a shared library (cryptlib)"
date: 2013-06-25
forum: General Help
---

### Post by sefs on 2013-06-25
I have downloaded and compiled a share library to get "libcl.so.3.4.2"

I have placed this lib in an application directory /opt/syncterm/lib/libcl.so.3.4.2 and went and additional step of smlinking libcl.so to this.

I created a file /etc/ld.so.conf.d/libcrypt.conf and put in here "/opt/syncterm/lib"

I then ran sudo ldconfig.

then I checked with ldconfig -v | less and see this

```

/opt/syncterm/lib:
        libcl.so.3.4.2 -> libcl.so.3.4.2
/usr/lib/i386-linux-gnu/mesa:
        libGL.so.1 -> libGL.so.1.2
/lib/i386-linux-gnu:
        libcrypto.so.0.9.8 -> libcrypto.so.0.9.8
        libpcprofile.so -> libpcprofile.so
        libexpat.so.1 -> libexpat.so.1.5.2
        libkeyutils.so.1 -> libkeyutils.so.1.4
...
...
...

```

But when I run the app that is dependent on this lib it says it can't find the lib.

Is there anything I missed?

Thanks. :)

---

### Post by DeathByDenim on 2013-06-25
That's weird. Does that app start when you run it like this:
```
LD_LIBRARY_PATH=/opt/syncterm/lib app
```
where you replace app with the name of the executable of course.
Does ldd give some clues?
```
ldd app
```

---

### Post by sefs on 2013-06-25
> **DeathByDenim said:**
> That's weird. Does that app start when you run it like this:
```
LD_LIBRARY_PATH=/opt/syncterm/lib app
```
where you replace app with the name of the executable of course.
Does ldd give some clues?
```
ldd app
```

Hi, 

Thanks for the response.

Now when I run 

```
LD_LIBRARY_PATH=/opt/syncterm/lib /opt/syncterm/syncterm
```

It still says libcrypt cannot be found.

Now when I do this...
```
ldd /opt/syncterm/syncterm
```

It says this...

```

	linux-gate.so.1 =>  (0xf7736000)
	libutil.so.1 => /lib/i386-linux-gnu/libutil.so.1 (0xf7710000)
	libncurses.so.5 => /lib/i386-linux-gnu/libncurses.so.5 (0xf76ee000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf76e8000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf76bc000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf76a1000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf74f8000)
	libtinfo.so.5 => /lib/i386-linux-gnu/libtinfo.so.5 (0xf74d9000)
	/lib/ld-linux.so.2 (0xf7737000)

```

I can't see the library there...

---

### Post by DeathByDenim on 2013-06-25
Ah ok. The fact that it doesn't show up in ldd, means that the program itself is probably trying to load the library dynamically. The program is likely not looking at all at the library path for libcl.so, but instead looking in some very specific directory that is hard-coded into the program.

Did you compile the program yourself? There might be an option somewhere in the Makefile to specify the library directory. Or if the source comes with "configure" then you can run 
```
./configure --help
```
Failing that, you can look in the source for "dlopen", which is how dynamic libraries are opened.

---

### Post by sefs on 2013-06-25
> **DeathByDenim said:**
> 
Did you compile the program yourself? 
Failing that, you can look in the source for "dlopen", which is how dynamic libraries are opened.

No I didn't, I downloaded it as a binary.  But The src is also available, I will give configure help a whirl and see what it says.  Also will try to see if i see any references to dlopen.

---

### Post by DeathByDenim on 2013-06-25
Oh, a little warning though. dlopen references are a bit hard to understand if you are not a programmer, but with any luck the path  actually hard-coded there. You can get all references to dlopen with this command:
```
grep -R dlopen src
```
where you need to replace src with the directory where you downloaded the sources to. Where did you download the program from? I can have a look as well then.

---

### Post by sefs on 2013-06-25
> **DeathByDenim said:**
> Oh, a little warning though. dlopen references are a bit hard to understand if you are not a programmer, but with any luck the path  actually hard-coded there. You can get all references to dlopen with this command:
```
grep -R dlopen src
```
where you need to replace src with the directory where you downloaded the sources to. Where did you download the program from? I can have a look as well then.

Gobbledegook...
```

./src/syncterm/syncterm.c:#include <xp_dl.h>	/* xp_dlopen() and friends */
./src/syncterm/syncterm.c:		shell32=xp_dlopen(shell32dll, RTLD_LAZY, 6);
./src/syncterm/syncterm.c:		ole32=xp_dlopen(ole32dll, RTLD_LAZY, 0);
./src/syncterm/st_crypt.c:	cryptlib=xp_dlopen(libnames,RTLD_LAZY, CRYPTLIB_VERSION/1000);
./src/syncterm/syncterm.man:run-time linking is employed using dlopen(). Using this, it is possible to
Binary file ./src/syncterm/gcc.linux.x64.obj.debug-mt/st_crypt.o matches
./src/conio/x_cio.c:	if((dl=xp_dlopen(libnames,RTLD_LAZY,7))==NULL)
./src/conio/sdlfuncs.c:	if((sdl_dll=xp_dlopen(libnames,RTLD_LAZY|RTLD_GLOBAL,SDL_PATCHLEVEL))==NULL)
./src/conio/sdl_con.c:		dl=xp_dlopen(libnames,RTLD_LAZY|RTLD_GLOBAL,7);
./src/xpdev/xpbeep.c:					|| ((dl=xp_dlopen(libnames,RTLD_LAZY,0))==NULL)
./src/xpdev/xpbeep.c:					|| ((dl=xp_dlopen(libnames,RTLD_LAZY,2))==NULL)
./src/xpdev/xp_dl.h:	DLLEXPORT dll_handle DLLCALL xp_dlopen(const char **name, int mode, int major);
./src/xpdev/xp_dl.h:	DLLEXPORT dll_handle DLLCALL xp_dlopen(const char **name, int mode, int major);
./src/xpdev/xp_dl.h:	#define xp_dlopen(name, mode, major)	(name)
./src/xpdev/xp_dl.c:DLLEXPORT dll_handle DLLCALL xp_dlopen(const char **names, int mode, int major)
./src/xpdev/xp_dl.c:		if((ret=dlopen(fname, mode))!=NULL)
./src/xpdev/xp_dl.c:		if((ret=dlopen(fname, mode))!=NULL)
./src/xpdev/xp_dl.c:		if((ret=dlopen(fname, mode))!=NULL)
./src/xpdev/xp_dl.c:			if((ret=dlopen(fname, mode))!=NULL)
./src/xpdev/xp_dl.c:		if((ret=dlopen(fname, mode))!=NULL)
./src/xpdev/xp_dl.c:		if((ret=dlopen(fname, mode))!=NULL)
./src/xpdev/xp_dl.c:			if((ret=dlopen(fname, mode))!=NULL)
./src/xpdev/xp_dl.c:DLLEXPORT dll_handle DLLCALL xp_dlopen(const char **names, int mode, int major)
./src/xpdev/sdlfuncs.c:	if((sdl_dll=xp_dlopen(libnames,RTLD_LAZY|RTLD_GLOBAL,SDL_PATCHLEVEL))==NULL)
Binary file ./src/xpdev/gcc.linux.x64.obj.debug-mt/xp_dl.o matches
Binary file ./src/xpdev/gcc.linux.x64.lib.debug/libxpdev_mt.a matches
./3rdp/src/cl/cryptlib.c:/* OS X Snow Leopard broke dlopen(), if it's called from a (sub-)thread then 
./3rdp/src/cl/cryptlib.c:   it dies with a SIGTRAP.  Specifically, if you dlopen() a shared library 
./3rdp/src/cl/cryptlib.c:   dlopen() checks if the thread is the main thread (specifically 
./3rdp/src/cl/cryptlib.c:   inability to call dlopen() from a thread was apparently a requirement in 
./3rdp/src/cl/kernel/init.c:	 and __DTOR_LIST__, they're called automatically before dlopen/dlclose
./3rdp/src/cl/kernel/init.c:		   functions are called before the main() is called or dlopen()
./3rdp/src/cl/misc/os_spec.h:    /* Older versions of OS X didn't have dlopen() support but required
./3rdp/src/cl/misc/os_spec.h:	   installed, get Peter O'Gorman's dlopen() implementation, which wraps
./3rdp/src/cl/misc/os_spec.h:	#define DynamicLoad( name )	dlopen( name, RTLD_LAZY )
./3rdp/src/cl/tools/buildall.sh:# OS X Snow Leopard broke dlopen(), if it's called from a (sub-)thread then it
./3rdp/src/cl/tools/buildall.sh:# dies with a SIGTRAP.  Specifically, if you dlopen() a shared library linked
./3rdp/src/cl/tools/buildall.sh:# CoreFoundation then the function CFInitialize() inside dlopen() checks if
./3rdp/src/cl/tools/buildall.sh:#	echo "This version of OS X Snow Leopard may have a buggy dlopen() that crashes" ;

```

---

### Post by sefs on 2013-06-25
Just an additional note.

Somehow I suspect it is looking for the specific name libcl.so.
I created a simlink to libcl.so.3.4.2 in the same directory.

but ldconfig still shows
/opt/syncterm/lib:
        libcl.so.3.4.2 -> libcl.so.3.4.2


not /opt/syncterm/lib:
        libcl.so -> libcl.so.3.4.2

If that's how it works not sure....

---

### Post by DeathByDenim on 2013-06-26
Hmm, I'm not sure either. I've looked at the file src/xpdev/xp_dl.c, where the library loading routine is and it looks like it tries to load libcl.so.3 first and if it fails, then libcl.so, so it should have worked. Maybe you can create an additional symlink to libcl.so.3?
```
cd /opt/syncterm/lib
sudo ln -s libcl.so.3.4.2 libcl.so.3
sudo ldconfig
```

By the way, when I ran it after compiling, the program just ran without complaining about libcl.so, even though I don't have it installed on my system. It just means there's no SSH support according to the man page.

You could try compiling the program yourself and see if it works then? You need to install libncurses5-dev using apt-get and then you can go to the src/syncterm directory and type:
```
make SRC_ROOT=`cd ..; pwd`
```

(I downloaded the source from [http://syncterm.bbsdev.net/syncterm-src.tgz](http://syncterm.bbsdev.net/syncterm-src.tgz) by the way)

---

### Post by Kujua on 2013-06-26
> **sefs said:**
> Just an additional note.

Somehow I suspect it is looking for the specific name libcl.so.
I created a simlink to libcl.so.3.4.2 in the same directory.

but ldconfig still shows
/opt/syncterm/lib:
        libcl.so.3.4.2 -> libcl.so.3.4.2


not /opt/syncterm/lib:
        libcl.so -> libcl.so.3.4.2

If that's how it works not sure....

I think "ldconfig -v" will show only the links created by ldconfig. Since libcl.so was created by you it is not printed, but might still be added to the cache.
Check the contents of the cache with:
```
ldconfig -p | grep libcl.so
```

---

### Post by sefs on 2013-06-27
Yup I tried compiling but ran into errors on 64 bit, I tried on 32 bit 12.04 and had to comment out some NameThread calls in the source before it would eventually compile, but still no SSH lol.

Wooooo


Now that I say that i wonder if I should try compiling the cryptlib source as a 32 bit shared library and see if that works.


KUJUA: I did what you said and it did show up in that command.  Thanks.

---

### Post by sefs on 2013-06-27
LOL.

Victory is ourrrrssss guys!!!

I compiled cryptlib on 10.04 32bit in a VM.  I put it in the /opt/syncterm/lib directory
I created two symlinks to it.  libcl.so.3 and libcl.so.

I ran sudo ldconfig launched syncterm and it connected using ssh :)

Thanks.  So in hindsight I probably needed to 1) compile as a 32 bit and 2) make a symlink to libcl.so.3 and libcl.so as you pointed out.  I dont even know how you found out where to look in the source code but you did it man!

Thanks :)

---

### Post by DeathByDenim on 2013-06-27
Quite a roundabout way, but I'm glad it worked. :)

It compiled fine on my Kubuntu 13.04 64-bit by the way. Although I didn't try compiling cryptlib.
Anyway, nice! :)

---

