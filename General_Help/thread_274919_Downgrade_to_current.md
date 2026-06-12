---
title: "Downgrade to current"
date: 2006-10-10
forum: General Help
---

### Post by JayMcNasty on 2006-10-10
I've added and now removed a few repositories notably Quinn's XGL site.  Because of this a few of my packages have become out of sync with official Ubuntu 6.06.  I would like to bring my system back into sync with official.  Could anyone please give me some pointers on what I would need to do in order to accomplish this?

---

### Post by Rhaurison Bergamin on 2006-10-10
> **JayMcNasty said:**
> I've added and now removed a few repositories notably Quinn's XGL site.  Because of this a few of my packages have become out of sync with official Ubuntu 6.06.  I would like to bring my system back into sync with official.  Could anyone please give me some pointers on what I would need to do in order to accomplish this?


for downgrade you need to force (use synaptic for this...) in main menu, Packages -> Force Version... a hard task because you need to do this package by package.
But first you must use default sources.list to try update/upgrade


deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper universe
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

