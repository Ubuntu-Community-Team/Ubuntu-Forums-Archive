---
title: "Eclipse + Subclipse on 7.04"
date: 2007-10-12
forum: General Help
---

### Post by sheppjr on 2007-10-12
For the past few days I've been trying to get Subclipse working in Eclipse on Feisty with no success... is there anywhere with a step-by-step guide to install it, or something like that?

It appears that the main problem was with JavaHL, which was not loading for some reason. The SVNKit plugin didn't work. Any help is appreciated.

---

### Post by jespdj on 2007-10-12
How are you installing Subclipse, are you doing it via the Eclipse update manager as described on the [Subclipse website](http://subclipse.tigris.org/)? ([Step by step instructions](http://subclipse.tigris.org/install.html)). That should work.

Which Java version are you using? And what version of Eclipse?

---

### Post by sheppjr on 2007-10-15
I am using the Eclipse update manager.


Eclipse v. 3.2
Subclipse v. 1.2.4
Java v. 1.6.0


Running Ubuntu 7.04 through VMware Server Console v. 1.0.4 on Windows Vista.

---

### Post by klevo on 2008-06-06
I too have a problem with Subclipse both on vanilla Eclipse (installed trough update manager) and with the Zend Studio for Eclipse which even comes with it's own Java version. Subclipse returns some PATHINFO error after trying to connect to a remote repository. Zend Studio returns no errors, but it's also unable to connect to any remote repository.

SVN from command line works like charm.

This started after I moved from Feisty 32bit to Herdy 64bit. (Clean install.)

---

