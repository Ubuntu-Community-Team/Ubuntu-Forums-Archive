---
title: "apt-build set to '-O3' but still compiling with '-O2'"
date: 2007-11-01
forum: General Help
---

### Post by michelinux on 2007-11-01
Hi, I configured my apt-build to compile using the -03 optimization, as you can see in my apt-build.config:
```
build-dir = /var/cache/apt-build/build
repository-dir = /var/cache/apt-build/repository
Olevel = -O3
mtune = -mtune=athlon-tbird
options = " "
make_options = " "
```
Actually when I try to rebuild and install a program, e.g. faac:
```
sudo apt-build --reinstall install faac
```
I can see that the all compilation process will use the **-02 **options instead of the **-03**.
Why is this happening, and what can I do to change this behaviour?
Thanks, I love you all.

---

