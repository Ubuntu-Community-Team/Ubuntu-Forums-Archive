---
title: "Why have there been so many kernel updates recently?"
date: 2014-07-26
forum: General Help
---

### Post by SeijiSensei on 2014-07-26
Maybe it's my imagination, but it does seem we are getting new kernel releases for 14.04 very frequently.  Are these all newly-discovered security flaws that have been fixed, or are they largely minor changes to the kernel to add drivers, etc.?  

The [changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/linux_3.13.0-32.57/changelog") has lots of new releases marked "urgency=low," yet Kubuntu continues to warn me about needing security updates every time a new kernel is released.  Why even identify something as having "low" urgency if the operating system acts as though urgency is always "high?"

---

### Post by slooksterpsv on 2014-07-26
The kernel itself is a major part of the OS, so in theory, Kubuntu's update system could automatically flag newer kernels, no matter how small of an update, as a critical or high security update. You may want to take this up with the maintainers of Kubuntu.

---

### Post by mc4man on 2014-07-26
urgency is just for the launchpad build system's queue , nothing to do with what  the upgrade is about..

---

### Post by Yellow Pasque on 2014-07-26
Security updates and backported fixes from newer kernels...

---

