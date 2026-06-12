---
title: "Libary Issue"
date: 2012-12-06
forum: General Help
---

### Post by 3246251196 on 2012-12-06
```
ls -l /usr/lib/x86_64-linux-gnu/ | grep libopenal
```produces:

```
lrwxrwxrwx 1 root root       14 Mar  6  2012 libopenal.so -> libopenal.so.1
```A link to absolutely nothing. When I try and compile a program, understandably the linker says there is no such library.

Before this, I ran:

```
apt-get install libopenal-dev
``````
apt-file show libopenal-dev
```Produces:

```
libopenal-dev: /usr/include/AL/al.h
libopenal-dev: /usr/include/AL/alc.h
libopenal-dev: /usr/include/AL/alext.h
libopenal-dev: /usr/include/AL/efx-creative.h
libopenal-dev: /usr/include/AL/efx.h
libopenal-dev: /usr/lib/x86_64-linux-gnu/libopenal.so
libopenal-dev: /usr/lib/x86_64-linux-gnu/pkgconfig/openal.pc
libopenal-dev: /usr/share/doc/libopenal-dev/README.Debian
libopenal-dev: /usr/share/doc/libopenal-dev/changelog.Debian.gz
libopenal-dev: /usr/share/doc/libopenal-dev/copyright
```EDIT:::

Trying to debug a program, I have had to install different version of openal, they were installed using cmake - which installed to the prefix usr/local, rather than the usr prefix that apt-get installed openal to. But, I "rm" every file in the cmake manifest. i think, to ensure, remove all from al-dev and alut-dev packages, then reinstall them. now, everytime, i get no actual library for openal, just a link to absolutely nothing.

Thanks.

```
/usr$ find . -iname "*openal*"
./share/doc/libopenal-dev
./share/doc/libopenal-data
./share/doc/libopenal1
./share/cmake-2.8/Modules/FindOpenAL.cmake
./lib/x86_64-linux-gnu/wine/openal32.dll.so
./lib/x86_64-linux-gnu/wine/fakedlls/openal32.dll
./lib/x86_64-linux-gnu/libopenal.so
./lib/x86_64-linux-gnu/pkgconfig/openal.pc
./lib/x86_64-linux-gnu/gstreamer-0.10/libgstopenal.so
./lib/i386-linux-gnu/wine/openal32.dll.so
./lib/i386-linux-gnu/wine/fakedlls/openal32.dll
```

---

### Post by 3246251196 on 2012-12-06
Anyone?

---

### Post by 3246251196 on 2012-12-06
Dependency hell was the issue here. I removed all that was linked to openal, and re-installed packages that I needed. It would have been nice to avoid such a drastic removal and this could have been done with more research. But, it all worked out in the end using, what apt-get is build upon, dpkg.

---

