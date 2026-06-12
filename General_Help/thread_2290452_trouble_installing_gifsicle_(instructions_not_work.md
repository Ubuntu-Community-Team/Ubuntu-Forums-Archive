---
title: "trouble installing gifsicle (instructions not working)"
date: 2015-08-12
forum: General Help
---

### Post by h8chanz on 2015-08-12
I'm trying to install this package right here: [https://github.com/kohler/gifsicle](https://github.com/kohler/gifsicle) but the installation instructions aren't working.

In the INSTALL file it says to cd to the directory and type in "./configure"

So that's what I do. But I get an error saying that it's an unrecognized command. There is a configure.ac file there, so I also try typing in ./configure.ac without any luck.

---

### Post by howefield on 2015-08-12
Try without the quotes or if you are not using quotes try using sh ./configure

Also just to point out that gifsicle is in the repository so is easy to install with apt, in case you weren't aware.

---

### Post by steeldriver on 2015-08-12
If you scroll down the main github page, it says

> 
**Building Gifsicle on UNIX**

  Type ./configure, then make.
**   If ./configure does not exist (you downloaded from Github), run autoreconf -i first.**


You could also run the provided bootstrap.sh script - which just contains the autoreconf command:

```

./bootstrap.sh

```

---

