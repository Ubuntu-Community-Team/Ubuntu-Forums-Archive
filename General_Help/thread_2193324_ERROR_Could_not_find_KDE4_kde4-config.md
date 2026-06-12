---
title: "ERROR: Could not find KDE4 kde4-config"
date: 2013-12-12
forum: General Help
---

### Post by silvercats on 2013-12-12
Ubuntu 12.04. I was trying to install KDBG with cmake.

---

### Post by drmrgd on 2013-12-12
Is this the same package as this:

[http://www.kdbg.org/index.php](http://www.kdbg.org/index.php)

If so, do you have KDE installed?  You mention Ubuntu 12.04, and if it's a stock install, then it's probably running the Unity and not KDE, which is why you're getting that error.

---

### Post by silvercats on 2013-12-12
How to find if it is unity ?

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) . This is the one I installed.

yes that is the KDBG package.

---

### Post by drmrgd on 2013-12-13
If you've installed the default Ubuntu system from the link, then you're likely running Unity (you probably have an applications bar on the left side of your screen for example).  You'll need to install KDE as the instructions indicate, but just so you're aware, this will completely change your entire desktop environment.

To install KDE, here is the official documentation, which is a bit lean on details:

[https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)

In short, you'll basically just need to install the 'kubuntu-desktop' package using either the Software Center or the commandline:

```

sudo apt-get install kubuntu-desktop

```

---

### Post by silvercats on 2013-12-13
Thanks!

---

