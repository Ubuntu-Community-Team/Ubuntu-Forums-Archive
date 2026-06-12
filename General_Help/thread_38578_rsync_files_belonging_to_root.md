---
title: "rsync files belonging to root"
date: 2005-06-01
forum: General Help
---

### Post by sornen on 2005-06-01
I was wondering if it is possible to use ssh for rsyncing files belonging to root on two computers without having to create the root user.  I cannot think of a way to do this.  Any suggestions greatly appreciated.

---

### Post by Mez on 2005-06-01
the -o flag with rsync will preserve owner of the file (can onl be used by root)

---

### Post by sornen on 2005-06-01
The problem though is you cannot log on as root when using rsync since root does not exist in the standard ubuntu setup.

---

