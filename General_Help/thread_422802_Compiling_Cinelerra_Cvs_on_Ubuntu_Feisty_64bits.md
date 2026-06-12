---
title: "Compiling Cinelerra Cvs on Ubuntu Feisty 64bits"
date: 2007-04-25
forum: General Help
---

### Post by DanielG007 on 2007-04-25
Hello, I have a problem with compiling cinelerra, i have downloaded the source code of cvs.cinelerra.org but i can't compile it, I use Feisty 64bits.

me -Wl,libquicktimehv-1.6.0.so.1 -o .libs/libquicktimehv-1.6.0.so.1.0.0
/usr/bin/ld: ffmpeg/libavcodec/.libs/libavcodec.a(mpegvideo_mmx.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
ffmpeg/libavcodec/.libs/libavcodec.a(mpegvideo_mmx.o): could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libquicktimehv.la] Error 1
make[3]: se sale del directorio `/home/dani/pandodl-16837/hvirtual/quicktime'
make[2]: *** [all-recursive] Error 1
make[2]: se sale del directorio `/home/dani/pandodl-16837/hvirtual/quicktime'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/dani/pandodl-16837/hvirtual'
make: *** [all] Error 2
root@amd64:/home/dani/pandodl/hvirtual# 


Any solution?

---

