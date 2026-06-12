---
title: "single &quot;unstable&quot; packages?"
date: 2007-04-04
forum: General Help
---

### Post by deinstein on 2007-04-04
hi!

sorry for being noob, I just installed kubuntu on my mum's pc, I myself use gentoo.

How can I only use a single unstable package (gutenprint, I need the new printer-drivers in 5.1.0), without going to unstable with the entire pc?

Thanks!!

deinstein

---

### Post by Ramses de Norre on 2007-04-04
Search a deb file for it and install it using ```
sudo dpkg -i *package.deb*
```
If you can't find a deb you can use the alien package to convert an rpm to a deb or use the same tools as you use on gentoo to compile from source.

---

### Post by az on 2007-04-04
Ubuntu is not binary-compatible.  You cannot use a package that is made for another release of Ubuntu or another distro.

Find the source and compile it using the toolchain included with your current release.

---

