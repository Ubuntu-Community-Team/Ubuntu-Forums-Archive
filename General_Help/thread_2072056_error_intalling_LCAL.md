---
title: "error intalling LCAL"
date: 2012-10-17
forum: General Help
---

### Post by kolibri on 2012-10-17
Trying to install lcal 2.1.0 from sourceforge.
[http://sourceforge.net/projects/pcal/files/pcal/lcal-2.0.0/](http://sourceforge.net/projects/pcal/files/pcal/lcal-2.0.0/)

pcal is in the Universe repository, lcal doesn't seem to be.

installation instructions:

make
sudo make install

make goes ok.

make install leads to the following error.

```
nroff -man ./lcal.man > ./lcal.cat
./lcal.man:59: warning [p 1, 1.5i]: can't break line
groff -man -Tps ./lcal.man >./lcal-help.ps
groff -man -Thtml ./lcal.man >./lcal-help.html
groff: can't find `DESC' file
groff:fatal error: invalid device `html' (try installing the `groff' package?)
make: *** [man] Error 3

```

any help?

Thanks.

---

### Post by spjackson on 2012-10-17
> ```

groff:fatal error: invalid device `html' (try installing the `groff' package?)

```By default groff-base is installed. To generate html you need the full groff package.
```

sudo apt-get install groff

```

---

