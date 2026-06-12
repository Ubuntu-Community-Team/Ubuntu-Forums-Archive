---
title: "Which softwares are missing?"
date: 2019-06-17
forum: General Help
---

### Post by parshwa23 on 2019-06-17
Hi,

I installed 'Ubuntu 18.04.2 LTS' with the option of 'minimal install' (due to some time constraints earlier). But now, I want to know which softwares have not been installed which otherwise would have installed if I would have gone with full installation.

Thx.

---

### Post by PaulW2U on 2019-06-17
This rather obscure link lists the packages that are not installed: [https://people.canonical.com/~ubuntu-archive/seeds/ubuntu.bionic/desktop.minimal-remove](https://people.canonical.com/~ubuntu-archive/seeds/ubuntu.bionic/desktop.minimal-remove) - when the minimal option is selected during installation.

Actually, I believe they **are** installed and **then** subsequently removed.   :)

---

### Post by CatKiller on 2019-06-17
A fairly straightforward way is to do ```
apt install --dry-run ubuntu-desktop
```
That will run through all the packages, and their dependencies, and their dependencies' dependencies, and so on, to show you what extra things would need to be installed to be running the default desktop rather than the minimal one.

---

### Post by corradoventu on 2019-06-18
the list of all packages in bionic is: 
[http://cdimages.ubuntu.com/bionic/daily-live/current/bionic-desktop-amd64.manifest](http://cdimages.ubuntu.com/bionic/daily-live/current/bionic-desktop-amd64.manifest)

---

### Post by parshwa23 on 2019-06-18
Well I check out...all these one by one....But when I ran:


> apt install --dry-run ubuntu-desktop


It showed the result as:


*********


> NOTE: This is only a simulation!
      apt needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version (1.417.1).


0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.


*********


which I believe is okay or nothing to be done from my side...

---

