---
title: "Determining how a package was built"
date: 2014-01-28
forum: General Help
---

### Post by DigiAngel on 2014-01-28
Hey all,

So here's my situation.  Currently running clamav-0.97.8, which is kind of old.  I'd like to replace this with the latest version.  I'd like to build it the same way that it was packaged.  Is there a site or somewhere that I can see what configure options and whatnot were used?  Thank you.

---

### Post by Dave_L on 2014-01-29
You can get the source package from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

This might be it, but the version may differ: [http://packages.ubuntu.com/source/precise/clamav](http://packages.ubuntu.com/source/precise/clamav)

The .tar.gz contains a makefile, which may have the information you need.

---

### Post by DigiAngel on 2014-01-30
That's just what I needed...thanks so much.

---

