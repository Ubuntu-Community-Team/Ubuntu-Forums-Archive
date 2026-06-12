---
title: "Is there a way to compile a program which uses outdated gtk?"
date: 2020-03-15
forum: General Help
---

### Post by insanity54 on 2020-03-15
I would like to install RSCW, a program which decodes morse code.

[https://www.pa3fwm.nl/software/rscw/](https://www.pa3fwm.nl/software/rscw/)

The problem I'm running into is that RSCW requires an old version of GTK, GTK 1.2.

Here is the output from my failed compilation attempt.

```
$ make
cc -O9 -g -Wall `gtk-config --cflags` rscwx.c -o rscwx `gtk-config --libs` -lm
/bin/sh: 1: gtk-config: not found
/bin/sh: 1: gtk-config: not found
rscwx.c:20:10: fatal error: gtk/gtk.h: No such file or directory
   20 | #include <gtk/gtk.h>
      |          ^~~~~~~~~~~
compilation terminated.
make: *** [Makefile:14: rscwx] Error 1

```

Things I have tried so far are installing libgth3-dev and libgtk2.0-dev, and neither of those seem to contain gtk/gtk.h. I don't see any gtk packages older than version 2 when I run `$ apt-cache search libgtk`



Is there a way to get an old version of gtk on my system? Is this a bad idea? Are there emulators or something similar which would allow me to install this sofware with outdated gtk? Is there some other method that I'm not considering?

---

### Post by u666sa on 2020-03-15
Sure!

[https://www.qsl.net/5b4az/pkg/morse/xdemorse/](https://www.qsl.net/5b4az/pkg/morse/xdemorse/)

Unpack

./configure
make
sudo checkinstall -D


[url=https://imgur.com/6GFOVmi.png]
  [img]https://imgur.com/6GFOVmi.png[/img]
[/url]


and enjoy endless evening of dot dash sessions!

---

### Post by HermanAB on 2020-03-15
Howdy,

My solution for old software, is to make a virtual machine with the correct old version of Linux, rather than messing up the up to date host with old libraries.

---

