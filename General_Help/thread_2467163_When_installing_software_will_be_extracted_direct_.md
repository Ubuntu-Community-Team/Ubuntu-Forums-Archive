---
title: "When installing software will be extracted direct to software path or a temp folder ?"
date: 2021-09-17
forum: General Help
---

### Post by aug7744 on 2021-09-17
When installing software using apt-get the deb files are extracted directly to software folder or first to a temp folder and after to software folder ?
If is extracted to a temp folder where is the path ?
I want create a writeback cache buffer if the deb files are extracted to a temp folder.

Have a nice day.

---

### Post by TheFu on 2021-09-17
Direct.
If you want to cache packages, check out apt-cacher-ng.

---

### Post by aug7744 on 2021-09-24
thanks

---

