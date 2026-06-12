---
title: "tar.xz to deb?"
date: 2014-04-22
forum: General Help
---

### Post by Autodave on 2014-04-22
Is there a program or command line to convert a .tar.xz to a .deb format?

---

### Post by MrBananaMan2011 on 2014-04-22
Have you tried CheckInstall?

When you install from source, instead of sudo make install, you would type sudo checkinstall.

More information here [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by HermanAB on 2014-04-23
Short answer: No.

A tar ball and a deb are not at all the same thing.  Debs have dependency information.

---

### Post by trag on 2014-04-26
You could attempt a conversion using Debriate, this is a link to the download and a 4 part video tutorial by the author of the program.  [http://debreate.sourceforge.net/](http://debreate.sourceforge.net/)
good luck
trag

---

### Post by 3rdalbum on 2014-04-26
What is the situation you are trying to deal with? There are several ways of compiling software from a .tar.gz into a Deb package.

---

