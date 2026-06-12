---
title: "gedit permissions"
date: 2008-06-21
forum: General Help
---

### Post by dnpate on 2008-06-21
ubuntu 8.04

gedit will not give me permission to replace (or save when changing the name) a file (samba.conf).  I cannot find a way to put in any password.  Also, I somehow lost access to my file manager and cannot find it.

---

### Post by lisati on 2008-06-21
Some files (including samba.conf) need "root" privileges to be active to be edited. Sometimes you need to use ```
sudo gedit <filename>
```

---

