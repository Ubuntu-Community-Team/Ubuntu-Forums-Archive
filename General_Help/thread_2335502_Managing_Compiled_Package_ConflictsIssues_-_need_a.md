---
title: "Managing Compiled Package Conflicts/Issues - need a starting point."
date: 2016-08-29
forum: General Help
---

### Post by dozy on 2016-08-29
Hello Everyone,

Thanks for taking the time to read this. I appreciate your assistance.
I am using Ubuntu 16.04

**My Question:**
What is the correct term for the issue I describe below? I have no problem doing the research to solve my problem, but I don't know its proper name, which means I don't know where to start. :-?

**The Issue:**
I decided to recompile Squid 3.5.x to include https (--enable-ssl, --enable-ssl-crtd, --with-openssl). So I downloaded the source from apt, added the config directives and recompiled the packages using dpkg-buildpackage. Everything worked correctly, I installed the resulting packages and all was well!

However, I then decided to install the normal repository version of squidguard. During its installation, it decided to install the repository version of squid, replacing the one I had manually compiled and installed.

It was at that point I asked the obvious question.. How do I manage this kind of scenario, where the normal package system seems to have no knowledge about, or wants to ignore, the packages I have manually compiled, and added to the system, in favor of its own repository versions? I imagine this issue is further complicated by installs that use **make** and **make install** to install software.

So I went looking and soon realized that I did not know what this issues is called, so I didn't get very far.
The only thing I found was how to **hold **a package in apt.

Can someone tell me what this issue/topic is called, and perhaps point me to a place I can learn more about it?

Thank you!

---

### Post by mc4man on 2016-08-29
When you rebuilt the debian package it used the debian/changelog as it was, i.e. it built the same package version as the repo. In those cases the repo package is always seen as an upgrade even though they are version-ed the same.

So you can look into how to create a new entry in debian/changelog, (I use dch -i ) or just open it up & edit the current one to be slightly higher. Typically adding a .1 will do though in this case a little different
This appears to be the current - 
```
quid3 (3.5.12-1ubuntu7.2) xenial-security; urgency=medium
```
So you'd make it quid3 (3.5.12-1ubuntu7.3~xenial) xenial-security; urgency=medium

The reason for the ~xenial is it will make it less than 3.5.12-1ubuntu7.3 (repo package) so if there is another security update you'll be informed a new version is available. 
(anything can go after the ~ for the example above I just used ~xenial. For my ppa's I typically use ~ppa

---

### Post by ian-weisser on 2016-08-30
One method of identifying locally-compiled software to the package manager is the 'checkinstall' package.

---

