---
title: "Configuration Management on Ubuntu"
date: 2007-09-23
forum: General Help
---

### Post by Nullack on 2007-09-23
So with Ubuntu releases you get a baseline set of packages that forms the build. Then security patches.

For things like upgrading to OO 2.3, latest Gnome and Nvidia drivers for example is it standard to wait until the next 6 monthly release of a new baseline? Or are the repositories updated in due course for things other than security patches?

Given I am new to Linux, do the experienced people stay up to date with stuff like new drivers and open office assuming that Ubuntu does not (within the same baseline release)? I guess that means having to learn how to package it yourself?

Thanks heaps and I look forward to being able to help out others once I learn more about Ubuntu :)

---

### Post by Martje_001 on 2007-09-23
> **Nullack said:**
> For things like upgrading to OO 2.3, latest Gnome and Nvidia drivers for example is it standard to wait until the next 6 monthly release of a new baseline?What you say ;). That's because it's not tested, and we don't want users to end up with an unstable system.

---

### Post by Wolki on 2007-09-23
> **Nullack said:**
> For things like upgrading to OO 2.3, latest Gnome and Nvidia drivers for example is it standard to wait until the next 6 monthly release of a new baseline? Or are the repositories updated in due course for things other than security patches?

You can enable the backports repository, which contains software from the next release that's repackaged to work on the previous release. This is often not easily possible, that's why it's not available for all software.

In general, waiting is the standard though. Ubuntu has a very quick release cycle, so you don't have to wait very long, and often special work is needed to make sure the software works as well as possible on ubuntu, in addition to another layer of bug-fixing.

---

### Post by Nullack on 2007-09-24
Thanks alot guys :) Understand that.

I look forward to contributing to the project (I have 12 years professional experience). Ive noticed the Canocial web apps are timing out so hopefully that will get fixed soon so I can register myself and get into it. I cant resist a bit of a Gutsy test so Im trying out the daily compile on a test machine. So much to learn :)

---

