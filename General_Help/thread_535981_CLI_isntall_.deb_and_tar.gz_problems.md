---
title: "CLI isntall .deb and tar.gz problems"
date: 2007-08-27
forum: General Help
---

### Post by Pitbull11188 on 2007-08-27
I installed ubuntu on a low-end system by doing a CLI install and then installing X and fluxbox as well as a few basic programs. My problem is apparently the CLI install does not include .deb compatibility and in fact even lacks a compiler.

So I was wondering the name of the packages I need to install to enable these features.

---

### Post by Seisen on 2007-08-27
In order to install .deb packages all you have to do is use dpkg like this

```
sudo dpkg -i packagename
``` and for building packages install build-essential.

```
sudo apt-get install build-essential
```

---

