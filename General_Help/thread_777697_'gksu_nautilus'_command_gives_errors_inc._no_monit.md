---
title: "'gksu nautilus' command gives errors inc. no monitor"
date: 2008-05-01
forum: General Help
---

### Post by MangasColoradas on 2008-05-01
Is this anything to be concerned about?

```
gksu nautilus
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:10771): WARNING **: Unable to add monitor: Not supported

```

---

### Post by jbc-wales on 2008-05-21
try gksudo nautilus, rather than sudo nautilus...

---

### Post by rfourie on 2008-10-05
i installed samba (not just samba-common) and it that solved it.

---

