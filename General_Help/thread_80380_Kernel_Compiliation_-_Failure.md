---
title: "Kernel Compiliation - Failure"
date: 2005-10-22
forum: General Help
---

### Post by duminas on 2005-10-22
OK, this is the third time I've tried this.
Using 2.6.11 sources from Aptitude (linux-tree-2.6.11), and my .config (named kern_config) is attached in a bzipped archive.

What's the problem, here? The tail it errors with is as follows:
```
  CC [M]  drivers/media/video/saa7134/saa7134-dvb.o
drivers/media/video/saa7134/saa7134-dvb.c: In function `dvb_init':
drivers/media/video/saa7134/saa7134-dvb.c:56: error: too few arguments to function `videobuf_dvb_register'
make[5]: *** [drivers/media/video/saa7134/saa7134-dvb.o] Error 1
make[4]: *** [drivers/media/video/saa7134] Error 2
make[3]: *** [drivers/media/video] Error 2
make[2]: *** [drivers/media] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.11'
make: *** [stamp-build] Error 2
```
Any help would be appreciated, since I've never figured this error out, and I've spent well over 10 hours on it so far in my attempts.

Thanks. ^^

---

