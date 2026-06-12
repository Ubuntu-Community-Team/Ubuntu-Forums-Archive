---
title: "apt vs aptitude in 8.04"
date: 2008-04-24
forum: General Help
---

### Post by dudinatrix on 2008-04-24
I've been using aptitude instead of apt for the past few releases because of something I read a while back regarding how they handle dependencies differently. I'm doing a fresh install of 8.04, and my question is does it really matter still? Is apt-get as good if not better than aptitude now?

---

### Post by prshah on 2008-04-24
> **dudinatrix said:**
> I've been using aptitude instead of apt for the past few releases because of something I read a while back regarding how they handle dependencies differently. I'm doing a fresh install of 8.04, and my question is does it really matter still? Is apt-get as good if not better than aptitude now?

aptitude is just a graphical front end to apt; it also accepts command line arguments, but if you don't specify any, opens up to a "mc" like interface.

---

### Post by kellemes on 2008-04-24
> **dudinatrix said:**
> I've been using aptitude instead of apt for the past few releases because of something I read a while back regarding how they handle dependencies differently. I'm doing a fresh install of 8.04, and my question is does it really matter still? Is apt-get as good if not better than aptitude now?

Nothing really has changed as far as I know..
Aptitude seems to handle dependencies differently indeed, can be seen as somewhat more efficient. I use aptitude myself, it works for me and like it's features.
Whatever you do, try not to mix the two. So make a choice and stick with it.

---

### Post by bakegoodz on 2010-05-30
aptitude has a all or nothing attitude for meta packages, apt does not.

For example remove ubuntu-desktop
aptitude will want to remove hundreds of dependent packages
apt will remove just remove the meta package, which sometimes I have do to cherry pick removal of unneeded packages.

---

