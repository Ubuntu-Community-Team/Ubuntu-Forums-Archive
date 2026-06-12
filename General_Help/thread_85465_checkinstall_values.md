---
title: "checkinstall values"
date: 2005-11-02
forum: General Help
---

### Post by stoeptegel on 2005-11-02
In compiled and made my own debian pwmanager package with checkinstall because i want to be able to manage my packages. 
There are some lines to fill in like maintainer and that stuff, i know some of them but if someone can make them explained i wouldn't make any mistakes.
Thanks.

0 -  Maintainer: [ [email]root@localhost.loca[/email]ldomain ]
1 -  Summary: [ PwManager made with checkinstall by stoeptegel ]
2 -  Name:    [ pwmanager-1.2.3 ]
3 -  Version: [ 1.2.3 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ pwmanager-1.2.3 ]
9 -  Alternate source location: [  ]

---

### Post by beefsprocket on 2005-11-02
Most of the time the default values are just fine. someimtes you'll come across a package that doesn't have a version number, just add whatever the number is on the tarball from which, in most cases, you've extracted the files. Accuracy is only as important as you feel necessary since the only person who will (or should) use the deb that you generate is you since it is tailored very much to your system's configuration and libraries. Most of that information is visible in synaptic or adept, but pretty much irrelevant if you know what it is that you have installed.

---

### Post by stoeptegel on 2005-11-02
So... checkinstall is only meant for local use and the debian packages for distribution are made with a total different tool. With alien?

---

### Post by beefsprocket on 2005-11-02
[quote=stoeptegel]So... checkinstall is only meant for local use and the debian packages for distribution are made with a total different tool. With alien?[/quote]

As I understand it, pbuilder is used to make the best .debs. I'm sure that for many packages checkinstall is fine, but the Debian New Maintainers' Guide, found here [http://www.debian.org/doc/maint-guide/ch-start.en.html](http://www.debian.org/doc/maint-guide/ch-start.en.html), sets out pbuilder as the maintainer's packager of choice.

---

### Post by stoeptegel on 2005-11-02
Ah got myself stuff to read, thank you. :)

---

### Post by shakin on 2005-11-03
You might want to remove the version number from the package's name, so the name would be 'pwmanager'. When there is a new version of pwmanager you do the same thing and dpkg will upgrade your existing package.

---

