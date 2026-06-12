---
title: "Kernel compile for mppe-patch"
date: 2005-08-30
forum: General Help
---

### Post by bindsocket on 2005-08-30
Okay...I went through the directions at [http://pptpclient.sourceforge.net/howto-debian-build.phtml](http://pptpclient.sourceforge.net/howto-debian-build.phtml) on how to build a new kernel with the mppe patch included.  However, everytime I have tried it, and with 3 different kernel sources, it has failed miserably.  I always get a 

```
START applying mppe patch (MPPE encryption support for PPP)
Testing whether "MPPE encryption support for PPP" patch for 2.6.10 applies (dry run):
patching file drivers/net/Kconfig
Hunk #1 succeeded at 2406 with fuzz 2 (offset 98 lines).
patching file drivers/net/Makefile
Hunk #1 FAILED at 101.
1 out of 1 hunk FAILED -- saving rejects to file drivers/net/Makefile.rej
The next patch would create the file drivers/net/arcfour.c,
which already exists!  Applying it anyway.
patching file drivers/net/arcfour.c
Patch attempted to create file drivers/net/arcfour.c, which already exists.
Hunk #1 FAILED at 1.
1 out of 1 hunk FAILED -- saving rejects to file drivers/net/arcfour.c.rej
The next patch would create the file drivers/net/arcfour.h,
which already exists!  Applying it anyway.
patching file drivers/net/arcfour.h
Patch attempted to create file drivers/net/arcfour.h, which already exists.
Hunk #1 FAILED at 1.
1 out of 1 hunk FAILED -- saving rejects to file drivers/net/arcfour.h.rej
patching file drivers/net/ppp_generic.c
Hunk #1 FAILED at 1045.
Hunk #2 FAILED at 1065.
Hunk #3 FAILED at 1590.
3 out of 3 hunks FAILED -- saving rejects to file drivers/net/ppp_generic.c.rej
The next patch would create the file drivers/net/ppp_mppe_compress.c,
which already exists!  Applying it anyway.
patching file drivers/net/ppp_mppe_compress.c
Patch attempted to create file drivers/net/ppp_mppe_compress.c, which already exists.
Hunk #1 FAILED at 1.
1 out of 1 hunk FAILED -- saving rejects to file drivers/net/ppp_mppe_compress.c.rej
The next patch would create the file drivers/net/sha1.c,
which already exists!  Applying it anyway.
patching file drivers/net/sha1.c
Patch attempted to create file drivers/net/sha1.c, which already exists.
Hunk #1 FAILED at 1.
1 out of 1 hunk FAILED -- saving rejects to file drivers/net/sha1.c.rej
The next patch would create the file drivers/net/sha1.h,
which already exists!  Applying it anyway.
patching file drivers/net/sha1.h
Patch attempted to create file drivers/net/sha1.h, which already exists.
Hunk #1 FAILED at 1.
1 out of 1 hunk FAILED -- saving rejects to file drivers/net/sha1.h.rej
patching file include/linux/ppp-comp.h
Hunk #1 succeeded at 285 with fuzz 1 (offset 94 lines).
"MPPE encryption support for PPP" patch for 2.6.10 does not apply cleanly
Patch /usr/src/kernel-patches/all/apply/mppe  failed.
``` 
I have tried the linux-source-2.6.11 and 2.6.10 (and 2.6.9 just to see)

 ](*,)   ](*,)    ](*,)

Brian

---

