---
title: "E: Sub-process /usr/bin/dpkg returned an error code (2)"
date: 2013-05-21
forum: General Help
---

### Post by helixo on 2013-05-21
```
Extracting templates from packages: 100%
dpkg: error: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
Setting up python-gnome2 (2.28.1+dfsg-1build1) ...
/var/lib/dpkg/info/python-gnome2.postinst: 5: /var/lib/dpkg/info/python-gnome2.postinst: /usr/share/python/runtime.d/python-gnome2.rtupdate: not found
dpkg: error processing python-gnome2 (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up python-support (1.0.15) ...
/var/lib/dpkg/info/python-support.postinst: 20: /var/lib/dpkg/info/python-support.postinst: update-python-modules: not found
dpkg: error processing python-support (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of screenlets-pack-basic:
 screenlets-pack-basic depends on python-support (>= 0.90.0); however:
  Package python-support is not configured yet.

dpkg: error processing screenlets-pack-basic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of screenlets:
 screenlets depends on python-support (>= 0.90.0); however:
  Package python-support is not configured yet.
 screenlets depends on python-gnome2; however:
  Package python-gnome2 is not configured yet.

dpkg: error processing screenlets (--configure):
 dependency problems - leaving unconfigured
Setting up libblas3 (1.2.20110419-5) ...
update-alternatives: error: alternative path /usr/lib/libblas/libblas.so.3 doesn't exist
dpkg: error processing libblas3 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of liblapack3:
 liblapack3 depends on libblas3 | libblas.so.3 | libatlas3-base; however:
  Package libblas3 is not configured yet.
  Package libblas.so.3 is not installed.
  Package libblas3 which provides libblas.so.3 is not configured yet.
  Package libatlas3-base is not installed.

dpkg: error processing liblapack3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-numpy:
 python-numpy depends on libblas3 | libblas.so.3 | libatlas3-base; however:
  Package libblas3 is not configured yet.
  Package libblas.so.3 is not installed.
  Package libblas3 which provides libblas.so.3 is not configured yet.
  Package libatlas3-base is not installed.
 python-numpy depends on liblapack3 | liblapack.so.3 | libatlas3-base; however:
  Package liblapack3 is not configured yet.
  Package liblapack.so.3 is not installed.
  Package liblapack3 which provides liblapack.so.3 is not configured yet.
  Package libatlas3-base is not installed.

dpkg: error processing python-numpy (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-gnome2
 python-support
 screenlets-pack-basic
 screenlets
 libblas3
 liblapack3
 python-numpy
```



the above thing is from "synaptic package manager"
this happens while installing packages . . . 
in fact my ubuntu software center also crashes very frequently , sometimes firefox also opens only google ,

---

