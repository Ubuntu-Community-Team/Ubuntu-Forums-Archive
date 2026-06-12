---
title: "update errors"
date: 2008-02-07
forum: General Help
---

### Post by jettapup on 2008-02-07
Recently upgraded to 7.10, and as normal update alerted me and did so, with the following error results:

E: /var/cache/apt/archives/libgs8_8.61.dfsg.1~svn8187-0ubuntu3.3_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/libgs.so.8.61')
E: /var/cache/apt/archives/openoffice.org-java-common_1%
3a2.3.0-1ubuntu5.3_all.deb: subprocess dpkg-deb --fsys-tarfile returned
error exit status 2

I assume E: is not the e: drive as in Dos. i did get to the file libgs8_8.61 but i was not allowed to delete it, due to a permission issue. I clicked on it and eventually got a message to update from the repository, which i allowed it to do and got the same error report

So do I have to navigate through the command line in terminal to delete it or just what what?

---

### Post by pointone on 2008-02-07
```
sudo apt-get clean
sudo apt-get update
sudo apt-get -f install
sudo apt-get upgrade
```

---

