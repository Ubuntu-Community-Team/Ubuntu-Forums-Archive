---
title: "i am unable to do make install..what is wrong? which package i need"
date: 2006-09-03
forum: General Help
---

### Post by dhoom on 2006-09-03
while installin vhcs2.4 i m unable to do make install..what is wrong with this?

---

### Post by ayoli on 2006-09-03
to do make install (compile programms) you need build-essential package
```
sudo apt-get install build-essential
```
then you need also root rights to run make install:
```
sudo make install
```

---

### Post by Ramses de Norre on 2006-09-03
What are the errors? Can you use just make?

---

### Post by Irony on 2006-09-03
I thought build essential was just a program to tell you what dependencies are necessary rather than a 'make' program;

[PHP]If you do not plan to build Debian packages, you don't need this
package.  Moreover this package is not required for building Debian
packages.

This package contains an informational list of packages which are
considered essential for building Debian packages.  This package also
depends on the packages on that list, to make it easy to have the
build-essential packages installed.[/PHP]

---

### Post by Ramses de Norre on 2006-09-03
build-essential is a meta package, i doesn't really contain anything but it has a lot of programs as dependency which are used to make debs or to compile from source.
So it's needed (or recommended) to install it when you're going to compile stuff. It'll install stuff like gcc and make and so on.

---

### Post by Irony on 2006-09-03
Which explains why I could never compile anything!

---

