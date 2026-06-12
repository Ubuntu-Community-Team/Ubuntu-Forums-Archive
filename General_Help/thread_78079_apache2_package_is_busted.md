---
title: "apache2 package is busted"
date: 2005-10-17
forum: General Help
---

### Post by activejeff on 2005-10-17
new install, I can't install Apache2-mpm-prefork because it is:

2.0.54-4ubuntu2

whereas apache2-common is instead at:

2.0.54-5ubuntu2

this makes it impossible to get php installed on ths system

---

### Post by activejeff on 2005-10-17
never mind, fixed it by uninstalling the -5 packages and re-installing mpm-prefork

I did get an additional error when installing that might be related to problems on the apt server:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libapache2-mod-python/libapache2-mod-python2.4_3.1.3-3ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libapache2-mod-python/libapache2-mod-python2.4_3.1.3-3ubuntu1_i386.deb)
  MD5Sum mismatch

---

