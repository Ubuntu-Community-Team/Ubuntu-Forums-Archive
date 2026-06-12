---
title: "Need to reinstall 16.04 in April, or just upgrade pre release version?"
date: 2016-02-23
forum: General Help
---

### Post by Tom_Carr on 2016-02-23
If I install the pre-release version of ubuntu 16.04, do I need to reinstall when the official version comes out in April, or can I just do all the software upgrades and get the same result?

---

### Post by deadflowr on 2016-02-23
Just keep updating it, and it'll be 16.04 for as long as you want to run 16.04.
No need to re-install.

---

### Post by howefield on 2016-02-23
Either way will get you to a final release. 

Doing a

```
cat /etc/lsb-release
```

on a 16.04 install at the moment will yield something like

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu Xenial Xerus (development branch)"
```

As you keep updating and get closer to the actual release date, the "*(development branch)*" tag will drop off.

---

