---
title: "x11 problem building R"
date: 2005-08-03
forum: General Help
---

### Post by jakemikey on 2005-08-03
I've been trying to compile R 2.1.1 from source. Configure runs fine:

./configure --with-BLAS --with-readline=no

...but when I run make, I get the following error:

In file included from devX11.c:64:
devX11.h:57:74: X11/Intrinsic.h: No such file or directory

Why don't I have Intrinsic.h?  What do I need to install to get it?  Is there anything else that might be causing this error?

Thanks,

Jake

---

### Post by Dimitri101 on 2005-08-05
Intrinsic.h is in the libxt-dev package, but to make life easy there is also the xlibs-dev package which installs everything you need to build X apps.

---

### Post by jakemikey on 2005-08-05
THANK YOU so much!!!  I knew there was a simple answer out there somewhere!

---

### Post by dumbbeatnix on 2005-08-08
Also had the same prob, keep up the good work your forum is excellent.

 :razz:  :razz:  :razz:

---

