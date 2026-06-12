---
title: "Tork"
date: 2007-03-30
forum: General Help
---

### Post by Andrew Sorensen on 2007-03-30
I installed tork via klik,  the link to the ubuntu packages on their website doesnt work :/
anway, to use tork, so i downloaded it and went to compile.
first i typed
sh ./configure
and i get this 

checking for libevent directory... configure: error: Could not find a linkable libevent. You can specify an explicit path using --with-libevent-dir

---

### Post by acormack on 2007-03-30
You could try downloading this package:

[http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/tork_0.12-0+3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/tork_0.12-0+3v1ubuntu0_i386.deb)

Assuming you are using edgy?


Alec

---

### Post by merado on 2007-10-06
I can't install TorK on ubuntu feisty.

Using the latest source code (TorK-0.20) and the [official instructions]("http://tork.sourceforge.net/wiki/index.php/FAQ") I get:

```
$ make -f Makefile.cvs
This Makefile is only for the CVS repository
This will be deleted before making the distribution

./admin/cvs.sh: 651: --version: not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
```

The .deb package from the previous post gives:

"Error: Dependency is not satisfiable: libgeoip1"

I've installed autoconf 2.61-3 and libgeoip1 1.3.17-1.1 via synaptic manager.

---

