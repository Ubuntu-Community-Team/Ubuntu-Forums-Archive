---
title: "Beryl"
date: 2007-03-28
forum: General Help
---

### Post by hamp69 on 2007-03-28
Im about to attempt to install Beryl, but there is 10+ files, which one is the actual installer?

[http://www.beryl-project.org/releases.php](http://www.beryl-project.org/releases.php)

---

### Post by bernied on 2007-03-28
I haven't done this manually, I've only used beryl with gentoo and emerge (the build system) takes care of dependencies. But, from what I remember, you definitely need this lot (or the .gz equivalents):

    * aquamarine-0.2.1.tar.bz2
    * beryl-core-0.2.1.tar.bz2
    * beryl-manager-0.2.1.tar.bz2
    * beryl-plugins-0.2.1.tar.bz2
    * beryl-settings-0.2.1.tar.bz2
    * beryl-settings-bindings-0.2.1.tar.bz2

These I'm not so sure of, but it may be that you need at least one of either emerald or heliodor:
    * emerald-0.2.1.tar.bz2
    * emerald-themes-0.2.1.tar.bz2
    * heliodor-0.2.1.tar.bz2

---

### Post by bernied on 2007-03-28
Maybe I didn't answer your question very well. There is no actual installer - these are source packages, which means you have to compile them yourself. This is maybe a bit daunting the first time, but does open up a new world.

In ubuntu, if you want to compile from source, you should install the build-essential package.
```
sudo apt-get build-essential
```this will give you a compiler, C libraries, kernel headers (I don't really know what they are either) and various utilities.

Then, for each of those files, you need to download, unpack and build. To unpack, use tar, to build, go into the new directory created when you unpacked the file, and do
```
make
```to compile, and
```
sudo make install
```to install

So, you'd need to do this for each of those zipped source packages, and maybe the order is important but I can't help you there.

---

### Post by bernied on 2007-03-28
The alternative is to wait until beryl is included in ubuntu. Version 0.21 is pretty early.

Maybe beryl is included in Feisty - is it?

---

### Post by eentonig on 2007-03-28
Actually, if you upgrade to Feisty, Beryl is in the repo's and works perfect (for me).

just 

did sudo apt-get install beryl

---

