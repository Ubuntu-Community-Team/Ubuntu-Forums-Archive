---
title: "Spca5xx (webcam drivers) installation"
date: 2006-07-11
forum: General Help
---

### Post by Ludwik on 2006-07-11
I try to install [Spca5xx](http://mxhaard.free.fr/) on my Dapper. I downloaded sources, read installation instructions, typed "sudo make" and got an error:

```
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/ludwik/spca5xx-20060501 CC=cc modules
make: *** /lib/modules/2.6.15-25-386/build: No such file or directory.  Stop.
make: *** [default] Error 2

```

What's wrong? What should I do?

---

