---
title: "Compiling stuff"
date: 2006-07-06
forum: General Help
---

### Post by Ptero-4 on 2006-07-06
Hi. I just downloaded the metacity, firefox & nautilus sources (via sudo apt-get source) and wanted to ask.
What I need to put after debian/rules in each one of those apps to compile them the debian way (using debian/rules and making debs out of those apps)?

---

### Post by joft on 2006-07-06
Hi,

I think what you are searching for is dpkg-buildpackage. Cd into a directory of an extracted package and type:

```
dpkg-buildpackage -rfakeroot -us -uc
```

Look at the man page for dpkg-buildpackage for the meaning of the options. The first option is needed, if you call this with normal user priviledges and not as root.

You might get errors saying that packages are missing (build dependencies). Then you have to install those (mostly "-dev") packages.

Oh, and last but not least: dpkg-buildpackage comes with the package "dpkg-dev".

---

