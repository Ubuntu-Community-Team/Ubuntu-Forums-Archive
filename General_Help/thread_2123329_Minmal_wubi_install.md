---
title: "Minmal wubi install?"
date: 2013-03-07
forum: General Help
---

### Post by frash23 on 2013-03-07
So i am looking for installing wubi without any window manager or graphical parts at all.
Just like ubuntu server, but through the wubi installer.

I came across somewhere (cant find it again) where they said something about editing a package in the wubi config, but i forgot.

Do any of you have any suggestions?

---

### Post by kclark on 2013-03-07
This might be what your looking for

[http://ubuntuforums.org/showthread.php?t=537870](http://ubuntuforums.org/showthread.php?t=537870)

> **ago said:**
> Not directly, 1 because I would not run a production  server on top of a nested filesystem, 2 because wubi is for non-geeks.

That said you can edit c:\wubi\install\preseed.cfg and set the package to "ubuntu-standard".

That will install a minimal set of packages, good enough to get a useful  shell and enable you to install other packages, from there you can  install any other ubuntu-server specifc package you want

---

### Post by cortman on 2013-03-07
You could use the [Ubuntu minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") and Virtualbox to achieve much the same affect as well.

---

