---
title: "How to know that a app in ubuntu software is developed by ubuntu?"
date: 2020-07-12
forum: General Help
---

### Post by EngineerStrange on 2020-07-12
How to know that a app in ubuntu software is developed by ubuntu?):P

---

### Post by Dennis N on 2020-07-12
Try **apt show <package-name>**

Example:

```
dmn@Sydney-vm:~$ apt show gimp
Package: gimp
Version: 2.10.18-1
Priority: optional
Section: universe/graphics
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>

```

---

### Post by QIII on 2020-07-12
That indicates that the *package* is maintained by Ubuntu developers.  That is, some application is *packaged* for inclusion in the Ubuntu repos.  Although open source, the app itself may be unchanged from the original developed by somebody else.  It may have been changed significantly.  That is hard to determine.  GIMP, the app, is maintained by a group of open source volunteers and distributed as source code to the various developers of Linux distributions.

By the way, *Ubuntu* is an OS.  It does not develop anything.  The company that produces Ubuntu is Canonical, LTD.  Canonical does development.

You will likely find few apps developed solely by Canonical.  That's not the way the Linux community works.

In this case, being in the Universe repository, the package is maintained by a MOTU (Master of the Universe) -- usually a volunteer -- who maintains a package containing a third-party, often widely available, application.

---

### Post by Dennis N on 2020-07-12
A little further down, is 'Homepage' which is probably The Origin of the actual code.

```
dmn@Sydney-vm:~$ apt show gimp | grep -i homepage
Homepage: https://www.gimp.org/

```

---

