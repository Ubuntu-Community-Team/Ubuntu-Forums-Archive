---
title: "dpkg error 'dpkg --configure -a' to correct."
date: 2015-07-20
forum: General Help
---

### Post by fall2 on 2015-07-20
So I get this error when trying to run Synaptic package manager:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I type 'dpkg --configure -a' in a Terminal and get:

dpkg: error: requested operation requires superuser privilege

---

### Post by QIII on 2015-07-20
Hello!

You'll need to preface that with sudo to elevate your privileges.

```
sudo dpkg --configure -a
```

Cheers!

---

### Post by fall2 on 2015-07-20
Wow that was easy. It didn't look like it did anything but it fixed it. 

Thanks QIII

---

