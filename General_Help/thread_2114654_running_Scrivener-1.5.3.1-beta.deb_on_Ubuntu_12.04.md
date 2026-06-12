---
title: "running Scrivener-1.5.3.1-beta.deb on Ubuntu 12.04 (32 bit)"
date: 2013-02-10
forum: General Help
---

### Post by dragonfly41 on 2013-02-10
I've successfully run earlier beta's of Scrivener on Ubuntu 12.04 ..
but I can't get the latest 1.5.3.1-beta to launch after installing

> 
Scrivener is a powerful content-generation tool for writers  that allows you to concentrate on composing and structuring long and  difficult documents.

Any user of Scrivener got this app running on Ubuntu 12.04 32 bit?

One theory read in Scrivener forum is that there seems to be some incompatibility of Qt libraries  between Ubuntu 12.04 and Scrivener.

Scrivener uses earlier release of Qt libraries?

I've tried copying the Ubuntu Qt library from /usr/lib/i386-linux-gnu/
into /usr/share/scrivener/lib/
but that didn't work.

---

### Post by dragonfly41 on 2013-02-11
Can I rephrase the question?

In Ubuntu 12.04 how can I _downgrade_ Qt 4.8.1 to Qt 4.8.0 ?

and then later _upgrade_ from Qt 4.8.0 to Qt 4.8.1?

There was a suggestion posted here in similar circumstances ...

[https://isis.astrogeology.usgs.gov/IsisSupport/index.php?PHPSESSID=9msi046m6o28fiujhd0q61qkq3&/topic,3518.msg14039.html#msg14039](https://isis.astrogeology.usgs.gov/IsisSupport/index.php?PHPSESSID=9msi046m6o28fiujhd0q61qkq3&/topic,3518.msg14039.html#msg14039)

setting LD_LIBRARY_PATH to load the crashing application library first (Qt 4.8.0) _before_ the core libraries (Qt 4.8.1).

Would this work?

---

### Post by Untold on 2013-03-07
I also have an issue with the QT libraries.  I can get it to launch with no problem.  I have tried to use some features to see if they work.  When I try to import a .txt file, it crashes and I get the following:

```
Cannot mix incompatible Qt library (version 0x40803) with this library (version 0x40800)
Aborted (core dumped)
```

It is really frustraing. I really want to use this app as I have been searching for a program to help me keep track of timelines, ideas, and characters and it may just be what I am looking for.

I am running 12.10 on an HP mini.

---

