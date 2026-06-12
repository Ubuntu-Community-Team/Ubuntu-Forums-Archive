---
title: "compiling cinelerra... some errors"
date: 2006-11-12
forum: General Help
---

### Post by Man of Wax on 2006-11-12
Hello everyone!
In Edgy Eft when I try to compile cinelerra from source i got some errors.

```
wax@wax-desktop:~/cinelerra-2.1$ bash configure
CONFIGURING QUICKTIME
[: 22: ==: unexpected operator
[: 27: ==: unexpected operator
./configure: 39: Syntax error: Bad fd number
CONFIGURING LIBMPEG3
configure: line 139: cd: libmpeg3*: Nessun file o directory
CONFIGURING FFTW
configure: line 142: cd: fftw*: Nessun file o directory
CONFIGURING MJPEGTOOLS
configure: line 145: cd: mjpegtools*: Nessun file o directory
CONFIGURING SNDFILE
configure: line 150: cd: libsndfile*: Nessun file o directory
CONFIGURING RAW1394
configure: line 153: cd: libraw1394*: Nessun file o directory
CONFIGURING AVC1394
configure: line 159: cd: libavc1394*: Nessun file o directory
CONFIGURING IEC61883
configure: line 165: cd: libiec61883*: Nessun file o directory
CONFIGURING THEORA
configure: line 173: cd: libtheora*: Nessun file o directory
Writing hvirtual_config.h
Have Video4Linux 2
Have DVB
Don't have OpenGL 2.0
Configured successfully.  Type 'make' to build it.
wax@wax-desktop:~/cinelerra-2.1$ make
make -f build/Makefile.cinelerra
sh: Syntax error: end of file unexpected (expecting "then")
make[1]: Entering directory `/home/wax/cinelerra-2.1'
gcc -c -O2 -fomit-frame-pointer -falign-loops=2 -falign-jumps=2 -falign-functions=2 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -I../../freetype-2.1.4/include -I../../ -DHAVE_OSS -DHAVE_FIREWIRE  soundtest.c -o i686/soundtest.o
Assembler messages:
FATAL: can't create i686/soundtest.o: Nessun file o directory
make[1]: *** [i686/soundtest.o] Error 1
make[1]: Leaving directory `/home/wax/cinelerra-2.1'
make: *** [all] Error 2

```

I tried to install cinelerra both from .deb packages and repository but they dind't work...
Some advice?

Bye and thank you ^_^ (sorry for my english :???: )

---

### Post by ColinG on 2006-11-12
This won't help other than to perhaps stop you wasting your time. Cinelerra crops up on this group often but I have never seen anybody crack the compilation. It is strange that it is not in the repositories as the current version is useable (although Kino is more robust/bug free imo).

There are some distros that have Cinelerra available to them. Those that I know are:

Mandriva 2007
Fedora Core 6
PClinuxOS

I have experience of Cinelerra in Fedora and PCLinuxOS. They work pretty well but bugs are still there. The app can and does crash for no apparent reason 

Have you tried Kino?

---

### Post by Man of Wax on 2006-11-12
ok thank you for your help. 
I have just installed Kino and it seems to work well for my needs ;)

---

