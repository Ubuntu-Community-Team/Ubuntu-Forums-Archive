---
title: "re-package ubuntu"
date: 2007-09-01
forum: General Help
---

### Post by jokr004 on 2007-09-01
Hey, I'm looking for a way to add packages to ubuntu/debian and repackage it, is there an easy way to do this?  or am I better off doing LFS?

---

### Post by capink on 2007-09-01
I don't understand what you want exactly. If what you are asking for is  making deb package out of those already installed on your system, here you go:

1. Install dpkg-repack

```
sudo apt-get install dpkg-repack
```

2. repackage whatever package you want:

```
sudo dpkg-repack packagename
```

---

### Post by jokr004 on 2007-09-01
sorry, I guess I was pretty vauge.  well, what i want to do is install an ubuntu system, add packages and configure things in it and then repackage that as an installable system.  Either that, or is there a place in the ubuntu install cd where debs and sources are kept that I can just add to?

my other option is to use LFS (linux from scratch)

---

### Post by rsambuca on 2007-09-01
You want a program called "reconstructor".  You customize everything and make a cd.

---

### Post by jokr004 on 2007-09-01
yeah, I've looked into reconstructer, but is that the only application I can do this with?

---

### Post by rsambuca on 2007-09-01
Perhaps if you let us know what the problems are that you had with reconstructor.

---

### Post by jokr004 on 2007-09-01
well, can you add packaged with reconstructor?  I know you can add repos, but I've never seen anything about individual packages, especially not sources.

---

### Post by rsambuca on 2007-09-01
You can add or remove custom repositories, as well as packages.  I am not sure what you mean sources (repositories?)

---

### Post by jokr004 on 2007-09-01
source packages, tar.gz

I want to pack in openmpi and sge and some custom scripts, it might just be a better idea to do from scratch

---

### Post by rsambuca on 2007-09-01
Geez, I don't know about that one!  Try out their forums and wiki.

---

### Post by capink on 2007-09-01
If you want to recompile the sources - in case you want to modify them - you can use the command

```
apt-get source packagename
```

that will download the source package into you current directory. You can then proceed to modify the source as you wish and them recompile it using ./configure && make && make install. Or better yet, you can create a new debian package using the command dpkg-buildpackage. Note that you will still need to download the build dependencies before being able to compile. This can be done using the command:

```
sudo apt-get build-dep
```

the you can recompile the package using the command  

```
dpkg-buildpackage -rfakeroot /path/to/the/sources
```

A detailed guide can be found [here]("http://www.debian.org/doc/maint-guide/")

---

