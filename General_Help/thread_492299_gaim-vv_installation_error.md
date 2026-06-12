---
title: "gaim-vv installation error"
date: 2007-07-04
forum: General Help
---

### Post by qwasi_nodough on 2007-07-04
Hi there,

I've tried installing Gaim-vv in Feisty following the instructions given here: [http://gaim-vv.sourceforge.net/install.html](http://gaim-vv.sourceforge.net/install.html)

Doing step 4:

GST-Jpeg2000 installation:

1) Download and save the gst-peg2000 tarball to your home directory
2) Extract it by doing tar xzf gst-jpeg2000-1.0.0.tar.gz
3) cd gst-jpeg2000-1.0.0
4) ./configure --prefix=/usr && make
5) su
6) make install
7) exit (the root environment)
8) gst-register
9) gst-inspect-i386 jpeg2000


I got this error:

.....
.....
In file included from gstj2k.c:27:
gstj2kdec.h:27:17: error: j2k.h: No such file or directory
make[1]: *** [libgstjpeg2000_la-gstj2k.lo] Error 1
make[1]: Leaving directory `/home/qwasi/gst-jpeg2000-1.0.0/src'
make: *** [all-recursive] Error 1

Can anyone help me make sense here?

Thanks a lot!

Cheers, Qwasi Nodough.

---

