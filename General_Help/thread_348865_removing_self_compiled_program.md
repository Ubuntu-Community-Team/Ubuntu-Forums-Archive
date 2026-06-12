---
title: "removing self compiled program"
date: 2007-01-29
forum: General Help
---

### Post by usien on 2007-01-29
how to remove a program that i compiled myself and then installed with make install?

---

### Post by Ramses de Norre on 2007-01-29
a) if there is an uninstall script in the tarball you can run it;
b) if not you'll need to manually search which files are installed were (you can find this on the app's site, in the install script/make file, ...) and remove them.

That's the mess with installing without a package manager...

---

### Post by phansiizwe on 2007-01-29
Try:

```
make uninstall
```

---

### Post by hikaricore on 2007-01-29
or...if you have the source you can simply run:

```
sudo make uninstall
```

From the source directory.

---

### Post by usien on 2007-01-29
> **Ramses de Norre said:**
> a) if there is an uninstall script in the tarball you can run it;
b) if not you'll need to manually search which files are installed were (you can find this on the app's site, in the install script/make file, ...) and remove them.

That's the mess with installing without a package manager...

i wanted to get gaim 2 beta 6 for which there is no package available for edgy :-)
I have installed it, i don't want to remove it yet, i asked out of curosity so that i can remove it when there is a ubuntu package for gaim 2 available.

---

### Post by TheWizzard on 2007-01-29
next time if you compile something: use checkinstall
this makes a deb file for you.

---

