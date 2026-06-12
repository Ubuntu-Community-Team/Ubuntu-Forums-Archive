---
title: "Problems after upgrade"
date: 2007-08-27
forum: General Help
---

### Post by sadrak on 2007-08-27
kate: error while loading shared libraries: libkatepartinterfaces.so.0: cannot open shared object file: No such file or directory


know this happend often after one upgrade:

in /usr/lib/ are invalid symlinks and many .so are missing ...

on a working system there are:
libkatepartinterfaces.so -> libkatepartinterfaces.so.0.0.0
libkatepartinterfaces.so.0 -> libkatepartinterfaces.so.0.0.0
libkatepartinterfaces.so.0.0.0

on this system there are:
libkatepartinterfaces.so -> libkatepartinterfaces.so.0.0.0


this happend with many .so ... currently i copied 72 files & symlinks from the working system to this one ... but the next upgrade will come in a few days ... why the upgrade delete needed files? what is wrong with my system? feisty with current upgrades ... system is ~2 month old ...

---

### Post by sadrak on 2007-08-31
OK, we clean the hdd and install ubuntu again ... now it has another crazy problem ... apt-get upgrade failed at one package, to fix that with apt & dpkg wont work, cause of the packagelist (dont know the exact filename) was a missing : in another packagedescription ... looks like hdd or ram is defect? how can i check both?

fsck.ext3 + ?

---

