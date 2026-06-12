---
title: "Trying to compile xtide on a shared server..."
date: 2020-01-20
forum: General Help
---

### Post by wrybread on 2020-01-20
**Edit: solved, and I'd post the route that fixed it but it was pretty convoluted and I'm not sure exactly what fixed it. Sorry for the clutter.**

I'm trying to install Xtide ([https://flaterco.com/xtide/installation.html](https://flaterco.com/xtide/installation.html)) on a shared server hosted by Dreamhost (Ubuntu 18.04.3 LTS). I've heard it's possible, but without being able to use apt or apt-get I'm a bit stumped.

Here's the sequence I'm trying:

```

mkdir tmp
cd tmp
wget https://flaterco.com/files/xtide/xtide-2.15.2.tar.bz2
tar -xvf xtide-2.15.2.tar.bz2
cd xtide-2.15.2
./configure --prefix=$HOME/local --enable-shared --enable-symbol-prefix --without-x --enable-local-files
make 
make install

```

(Note that I don't need the full package with the graphical elements, so using --without-x).

Configure is erroring out with:

```

checking tcd.h usability... no
checking tcd.h presence... no
checking for tcd.h... no
configure: error: cannot find tcd.h; try setting CPPFLAGS.

```

Normally I'd fix that with:

```

apt-get install zlib1g-dev
apt-get install libpng-dev

```

But I'm not sure how to include that when compiling on a shared server without access to root. 

**Edit: solved, and I'd post the route that fixed it but it was pretty convoluted and I'm not sure exactly what fixed it. Sorry for the clutter.**

---

