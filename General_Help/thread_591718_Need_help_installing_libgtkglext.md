---
title: "Need help installing libgtkglext"
date: 2007-10-25
forum: General Help
---

### Post by bungnati on 2007-10-25
Im trying to install pSX on my laptop and am getting this message
"error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory"
I cant find this in the package manager and when i search for it I only get the 64-bit version and also the .rpm files are not able to be opened

Any help is greatly appreciated
John

---

### Post by Maestro23 on 2007-10-25
> **bungnati said:**
> Im trying to install pSX on my laptop and am getting this message
"error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory"
I cant find this in the package manager and when i search for it I only get the 64-bit version and also the .rpm files are not able to be opened

Any help is greatly appreciated
John

For the .rpm issue, you have to convert it using the "alien" command.

> sudo alien -i

Installing software in Ubuntu: [http://www.psychocats.net/ubuntu/installingsoftware#rpm](http://www.psychocats.net/ubuntu/installingsoftware#rpm)

---

### Post by bungnati on 2007-10-25
Thanks Maestro worked perfectly

---

