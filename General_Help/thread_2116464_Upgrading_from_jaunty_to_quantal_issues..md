---
title: "Upgrading from jaunty to quantal issues."
date: 2013-02-15
forum: General Help
---

### Post by rapethegrape on 2013-02-15
Hi I have some issues..
I have a ubuntu 9.0.4 disk but it has jaunty on it and will not let me upgrade no matter what I do so I edited my source files to point  to quantal repositories and got the following errors
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages. E: Unable to correct dependencies
I have been on every forum around and tried all steps and not getting any good results
MY cd drive will not read cd so I can not download an iso and try a fresh install unfortunatly the only options I have is terminal upgrades.

---

### Post by dcstar on 2013-02-15
> **rapethegrape said:**
> Hi I have some issues..
I have a ubuntu 9.0.4 disk but it has jaunty on it and will not let me upgrade no matter what I do so I edited my source files to point  to quantal repositories and got the following errors
.........

You cannot "upgrade" by changing the repositories like that.

---

### Post by 3rdalbum on 2013-02-16
> **rapethegrape said:**
> Hi I have some issues..
I have a ubuntu 9.0.4 disk but it has jaunty on it and will not let me upgrade no matter what I do so I edited my source files to point  to quantal repositories and got the following errors
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages. E: Unable to correct dependencies
I have been on every forum around and tried all steps and not getting any good results
MY cd drive will not read cd so I can not download an iso and try a fresh install unfortunatly the only options I have is terminal upgrades.

Clever idea, but it won't work.

Your only option is a clean install. If your CD drive doesn't work, you can plug in an external CD drive, or install the Ubuntu 12.10 ISO onto a USB drive. I think 9.04 has a "create USB startup disk" program preinstalled, doesn't it? That's what you'd need to use.

---

