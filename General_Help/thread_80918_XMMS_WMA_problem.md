---
title: "XMMS WMA problem"
date: 2005-10-23
forum: General Help
---

### Post by andars on 2005-10-23
At first I downloaded [http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.4.1.tar.bz2](http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.4.1.tar.bz2)

However when trying to run make I got these errors:

> gcc -o libwma.so obj/xmms-wma.o obj/iir.o `xmms-config --libs` -L ffmpeg-strip-wma -lffwma -shared
/usr/bin/ld: obj/xmms-wma.o: relocation R_X86_64_32 can not be used when making a shared object; recompile with -fPIC
obj/xmms-wma.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[1]: *** [libwma.so] Error 1
make: *** [all] Error 2


I tried what appeared to be the newer version [http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.5.tar.bz2](http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.5.tar.bz2)  and it installed with no problems, however anytime I load a WMA file XMMS just crashes.

---

### Post by RikBlankestijn on 2005-11-03
Try to continue from here: [http://ubuntuforums.org/showthread.php?p=224845](http://ubuntuforums.org/showthread.php?p=224845)

---

