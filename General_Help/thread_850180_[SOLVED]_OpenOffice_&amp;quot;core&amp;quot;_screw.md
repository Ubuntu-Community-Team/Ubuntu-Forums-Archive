---
title: "[SOLVED] OpenOffice &amp;quot;core&amp;quot; screwed up"
date: 2008-07-05
forum: General Help
---

### Post by taminrob on 2008-07-05
When trying to install recommended updates, I received a message that I had several broken packages (all are related to OpenOffice).  So I went to synaptic package manager looked up broken packages and uninstalled them.  That part went well, but when I try to reinstall OpenOffice I receive the following error:

E: /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-1ubuntu2_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program/libpackage2.so')

What do I need to do to fix this?

---

### Post by nikgare on 2008-07-05
```
sudo apt-get clean
```

This will get rid of any cached files  - the openoffice ones seems to be corrupt.
Then you need to run **apt-get update** and then you can install openoffice

---

### Post by taminrob on 2008-07-05
Thanks alot!  That took care of it...installed with no other problems!

---

