---
title: "Trying to complie tclspice from source. Can't write to /usr/lib?"
date: 2006-12-05
forum: General Help
---

### Post by skylerweaver on 2006-12-05
I am trying to compile tclspice from source. I installed all of the packages that I didnt have with Synaptic.

I run
```
./configure --with-tcl --enable-experimental --enable-xspice
make tcl
sudo make install-tcl
```

Everything compiles, but when it tries to actually install it dies with:

```
/bin/sh ../../../mkinstalldirs /usr/local/lib/spice
/usr/bin/install -c -m 644 spice2poly/spice2poly.cm /usr/local/lib/spice
/usr/bin/install -c -m 644 digital/digital.cm /usr/local/lib/spice
/usr/bin/install -c -m 644 analog/analog.cm /usr/local/lib/spice
/usr/bin/install -c -m 644 xtradev/xtradev.cm /usr/local/lib/spice
/usr/bin/install -c -m 644 xtraevt/xtraevt.cm /usr/local/lib/spice
make[3]: Leaving directory `/home/skylerweaver/Desktop/tclspice/src/xspice/icm'
make[3]: Entering directory `/home/skylerweaver/Desktop/tclspice/src/xspice'
make[4]: Entering directory `/home/skylerweaver/Desktop/tclspice/src/xspice'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/skylerweaver/Desktop/tclspice/src/xspice'
make[3]: Leaving directory `/home/skylerweaver/Desktop/tclspice/src/xspice'
make[2]: Leaving directory `/home/skylerweaver/Desktop/tclspice/src/xspice'
/bin/sh ../mkinstalldirs /usr/lib /usr/share
/usr/bin/install -c -m 644 libspice.so /usr/lib /usr/share
/usr/bin/install: omitting directory `/usr/lib'
make[1]: *** [install-tclspice] Error 1
make[1]: Leaving directory `/home/skylerweaver/Desktop/tclspice/src'
make: *** [install-tcl] Error 2

```

The command that fails is 

```
/usr/bin/install -c -m 644 libspice.so /usr/lib /usr/share
```

Why? and more importantly, is there a workaround?

Thanks,
Skyler

---

### Post by wpshooter on 2006-12-05
have you tried using sudo before all of your commands ?

---

### Post by skylerweaver on 2006-12-05
I fixed it.

Somehow configure set one of the paths to "/usr/lib /usr/share" which is not allowed.

I fixed it with this:

```
perl -pi -w -e 's/\/usr\/lib\ \/usr\/share/\/usr\/lib\n#\/usr\/share/g;' `find ./ -name Makefile`
```

Thanks for the help.

---

