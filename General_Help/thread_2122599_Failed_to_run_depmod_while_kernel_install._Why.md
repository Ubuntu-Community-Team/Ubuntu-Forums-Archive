---
title: "Failed to run depmod while kernel install. Why?"
date: 2013-03-05
forum: General Help
---

### Post by MK567 on 2013-03-05
I have error while installing linux kernel: Failed to run depmod.
```

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-image-3.8.2-030802-generic (3.8.2-030802.201303031906) ...
[B]Running depmod.
Usage: lsmod
Failed to run depmod[/B]
dpkg: error processing linux-image-3.8.2-030802-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-3.8.2-030802-generic:
 linux-image-extra-3.8.2-030802-generic depends on linux-image-3.8.2-030802-generic; however:
  Package linux-image-3.8.2-030802-generic is not configured yet.

dpkg: error processing linux-image-extra-3.8.2-030802-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 linux-image-3.8.2-030802-generic
 linux-image-extra-3.8.2-030802-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What causes it or how can I get more verbose error output?

---

