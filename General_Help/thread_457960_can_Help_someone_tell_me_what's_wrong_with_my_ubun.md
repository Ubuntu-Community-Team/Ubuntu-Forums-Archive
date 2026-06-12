---
title: "can Help: someone tell me what's wrong with my ubuntu"
date: 2007-05-29
forum: General Help
---

### Post by xbobo on 2007-05-29
recently got this problem after I upgraded something thru Update manager


(Reading database ... 259359 files and directories currently installed.)
Unpacking mozilla-thunderbird (from .../mozilla-thunderbird_1.5.0.10-0ubuntu3_i386.deb) ...
Setting up linux-restricted-modules-2.6.20-16-generic (2.6.20.5-16.28) ...
Bus error (core dumped)
dpkg: error processing linux-restricted-modules-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.20-16-generic; however:
  Package linux-restricted-modules-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-restricted-modules-generic; however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up mozilla-thunderbird (1.5.0.10-0ubuntu3) ...
Please restart any running Thunderbirds, or you will experience problems.

Errors were encountered while processing:
 linux-restricted-modules-2.6.20-16-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-restricted-modules-2.6.20-16-generic (2.6.20.5-16.28) ...
Bus error (core dumped)
dpkg: error processing linux-restricted-modules-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.20-16-generic; however:
  Package linux-restricted-modules-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-restricted-modules-generic; however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-restricted-modules-2.6.20-16-generic
 linux-restricted-modules-generic
 linux-generic

---

### Post by kuja on 2007-05-29
It looks like Thunderbird went through fine, but not the restricted modules.

Perhaps the files were corrupt? Try running ```
sudo apt-get clean
``` and then ```
sudo apt-get install --reinstall linux-generic linux-restricted-modules-generic linux-restricted-modules-2.6.20-16-generic
```

Maybe this will fix the problem?

---

### Post by zvacet on 2007-05-29
```
sudo dpkg --configure -a
```

---

### Post by xbobo on 2007-05-30
try this:

sudo dpkg --configure -a

then: 

Setting up linux-restricted-modules-2.6.20-16-generic (2.6.20.5-16.28) ...
Bus error (core dumped)
dpkg: error processing linux-restricted-modules-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.20-16-generic; however:
  Package linux-restricted-modules-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-restricted-modules-generic; however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-restricted-modules-2.6.20-16-generic
 linux-restricted-modules-generic
 linux-generic

---

