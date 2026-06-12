---
title: "Mplayer - very strange compile error"
date: 2007-02-07
forum: General Help
---

### Post by SadaraX on 2007-02-07
EDIT: This issue has been fixed. The next day they came out with about 100 SVN commits and when I tried to recompile, everything was fine... I have absolutely clear idea what was the problem.

Hello everyone. I have a very strange error when I try to compile Mplayer from SVN. Now, normally I do not bug forums with these type of problems, but this one seems really strange. 

To start with, here is the error: 

```

ad_ffmpeg.c:161: warning: 'avcodec_decode_audio' is deprecated (declared at ../libavcodec/avcodec.h:2524)
cc -I.. -Inative -I../libmpdemux -I../stream -I../loader  -I../libavutil -I../libavcodec -I. -I.. -Wdeclaration-after-statement -O4 -march=k8 -mtune=k8 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -I/usr/include/directfb -I/usr/include -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -I/usr/include -I/usr/include/dvdnav -I/usr/include/freetype2 -I/usr/include -I/usr/include/liveMedia -I/usr/include/UsageEnvironment              -I/usr/include/BasicUsageEnvironment -I/usr/include/groupsock   -c -o vd_ffmpeg.o vd_ffmpeg.c
vd_ffmpeg.c: In function 'init':
vd_ffmpeg.c:390: warning: 'AVPaletteControl' is deprecated
vd_ffmpeg.c: In function 'init_vo':
vd_ffmpeg.c:527: error: 'PIX_FMT_YUV422' undeclared (first use in this function)
vd_ffmpeg.c:527: error: (Each undeclared identifier is reported only once
vd_ffmpeg.c:527: error: for each function it appears in.)
vd_ffmpeg.c:529: error: 'PIX_FMT_RGBA32' undeclared (first use in this function)
vd_ffmpeg.c: In function 'get_buffer':
vd_ffmpeg.c:620: warning: assignment from incompatible pointer type
vd_ffmpeg.c: In function 'decode':
vd_ffmpeg.c:752: warning: assignment from incompatible pointer type
vd_ffmpeg.c:776: warning: comparison of distinct pointer types lacks a cast
make[1]: *** [vd_ffmpeg.o] Error 1
make[1]: Leaving directory `/home/clifton/Sata/Linux/compile/mplayer/trunk/libmpcodecs'
make: *** [libmpcodecs/libmpcodecs.a] Error 2

```

First, the problem happens with any version of Mplayer from SVN I try. The earliest I tried was 21185, and the latest is 22168. I tried various versions in between them, 21200, 21500, 21800, 22000, 22100, and many others. They all had the same problem. The compile error occurs during the 'make' stage. I have tried using various ./configure --arguments, and I have tried it with NO arguments, but the result is the same. 

I tried this on two computers, one running Edgy and one running Breezy. They both have the exact same error. This error occurs consistently, spanning many source revisions, and I cannot tell why. I tried deleting the source files and grabbing completely new source from the SVN repository, but the problem persists. 

Perhaps the very strangest part of all this is that I compiled yesterday (and every day before) without this problem (or any others). My current version of mplayer claims to be yesterdays latest SVN version, 22167. When I try to compile this specific version, the 'make' compile stage fails.

I would love anyone's thoughts on the matter.

---

### Post by lloyd_b on 2007-02-07
First off - I would suggest posting this type of question in the Programming forum, rather than General Help, as you're more likely to get an answer for this type of question there.

Second - the error you're seeing is probably a result of your machine having an incorrect version of a header (.h) file.  Generally, anytime you see symbols in all uppercase (PIX_FMT...), it's a symbol that's defined in a header file (not always mind you).

Have you installed/updated/removed anything on the system recently?  It sounds like you had a good (i.e. working) copy of a header file, and something changed it. 

Lloyd B.

---

### Post by SadaraX on 2007-02-07
> **lloyd_b said:**
> First off - I would suggest posting this type of question in the Programming forum, rather than General Help, as you're more likely to get an answer for this type of question there.

Second - the error you're seeing is probably a result of your machine having an incorrect version of a header (.h) file.  Generally, anytime you see symbols in all uppercase (PIX_FMT...), it's a symbol that's defined in a header file (not always mind you).

Have you installed/updated/removed anything on the system recently?  It sounds like you had a good (i.e. working) copy of a header file, and something changed it. 

Lloyd B.

It just so happens that I did an apt-get update today. EDIT: I will check my dpkg.log files

---

