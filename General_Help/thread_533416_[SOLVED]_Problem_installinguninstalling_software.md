---
title: "[SOLVED] Problem installing/uninstalling software"
date: 2007-08-23
forum: General Help
---

### Post by SOULRiDER on 2007-08-23
Whenever I try to install or Uninstall any packages i get this error:

```
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `ext.1.gz' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `ext.1.gz' must be followed by colon
```

any ideas?

---

### Post by aysiu on 2007-08-24
Maybe [this](http://forums.debian.net/viewtopic.php?p=1687&sid=09e3151c812eba3dabddbe8e336b7145) might help.

---

### Post by SOULRiDER on 2007-08-24
YES! That worked great, thanks!

---

