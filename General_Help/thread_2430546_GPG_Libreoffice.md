---
title: "GPG Libreoffice"
date: 2019-11-03
forum: General Help
---

### Post by yotux on 2019-11-03
I have some files that are signed with gpg and require gpg to access them.  In Ubuntu 19.10 I can not access the files or link a GPG key to libre office.  This process work without issue in other distro like Manjaro, Arch.  Any help out be useful

---

### Post by TheFu on 2019-11-05
Whenever programs that used to work together stop after a move to 19.10, my first guess is always that snap packages are involved which break the interoperability.  It is just a guess.
Use 
```
snap list
```
to see of either gpg or LibreOffice are being distributed via snap.  If it is a snap package for either program, opening a bug report for the failed interaction will get the snap owner to fix it, maybe.

---

