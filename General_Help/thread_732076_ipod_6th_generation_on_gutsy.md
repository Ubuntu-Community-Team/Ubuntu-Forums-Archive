---
title: "ipod 6th generation on gutsy"
date: 2008-03-22
forum: General Help
---

### Post by coninsan on 2008-03-22
Hi 

I am trying to manage my music and videos on my Ipod classic 160gb 6g in linux with any program, but so far i havnt been able to get anything positive out of it.

i tried with gtkpod and rhtyhmbox but the only thing i got out of that was that now my ipod refuses to se and play my music and everything else, the music is still filling out diskspace but nothing more.

ive tried a few guides but none with a good result, anyone know how to get a 6g ipod to work on linux gutsy? :confused:

---

### Post by coninsan on 2008-03-22
ive just tried this guide: [http://ubuntuforums.org/showthread.php?t=619615&highlight=ipod+6th](http://ubuntuforums.org/showthread.php?t=619615&highlight=ipod+6th)

but i get this error when the package is being created.
```
libtool: install: warning: relinking `_gpod.la'
(cd /home/steffen/Skrivebord/libgpod-0.6.0/bindings/python; /bin/bash ../../libtool  --tag=CC --mode=relink gcc -g -O2 -o _gpod.la -rpath /usr/local/lib/python2.5/site-packages/gpod -module -avoid-version _gpod_la-gpod_wrap.lo -lgobject-2.0 -lglib-2.0 -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lgobject-2.0 -lglib-2.0 ../../src/libgpod.la )  
gcc -shared  .libs/_gpod_la-gpod_wrap.o  -L/usr/lib -lgdk_pixbuf-2.0 -lm -lgmodule-2.0 -ldl -lgobject-2.0 -lglib-2.0 -L/usr/local/lib -lgpod  -Wl,-soname -Wl,_gpod.so -o .libs/_gpod.so
/usr/bin/install -c .libs/_gpod.soT /usr/local/lib/python2.5/site-packages/gpod/_gpod.so
/usr/bin/install: setting permissions for `/usr/local/lib/python2.5/site-packages/gpod/_gpod.so': No such file or directory
/usr/bin/install -c .libs/_gpod.lai /usr/local/lib/python2.5/site-packages/gpod/_gpod.la
/usr/bin/install: setting permissions for `/usr/local/lib/python2.5/site-packages/gpod/_gpod.la': No such file or directory
/usr/bin/install -c .libs/_gpod.a /usr/local/lib/python2.5/site-packages/gpod/_gpod.a
/usr/bin/install: setting permissions for `/usr/local/lib/python2.5/site-packages/gpod/_gpod.a': No such file or directory
chmod 644 /usr/local/lib/python2.5/site-packages/gpod/_gpod.a
ranlib /usr/local/lib/python2.5/site-packages/gpod/_gpod.a
ranlib: could not create temporary file whilst writing archive: No more archived files

```

this is quite annoying at this point, nothing works and my ipod is useless at this point.. 
anyone HELP! [-o<

---

### Post by coninsan on 2008-03-22
Anyone?

---

### Post by szandor on 2008-03-24
> **coninsan said:**
> Anyone?

try this:

[http://www.soccio.it/michelinux/2008/01/27/gtkpod-09912-backport-for-ubuntu-gutsy-gibbon/](http://www.soccio.it/michelinux/2008/01/27/gtkpod-09912-backport-for-ubuntu-gutsy-gibbon/)

edit: by the way, i have the 80gb classic and everything seems to be stable so far.

---

