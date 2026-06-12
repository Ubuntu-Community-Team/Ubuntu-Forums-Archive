---
title: "unmarking ntfs"
date: 2008-01-23
forum: General Help
---

### Post by kryth on 2008-01-23
Here's my problem.  I had my vista h/d(ntfs) mounted and Unbuntu crashed. Now it's still marked as in use. Windows and Unbuntu can do anything with it. Tried vista disc and repair. Nothing! SO anyone have a clue as to how to unmark a h/d as in use. NTFS drive that is.

---

### Post by Borbus on 2008-01-23
To mount it in Ubuntu, use a normal mount command but add -o force so for example, if you're mounting /dev/sda1 to /media/sda1 type:
```
mount -o force /dev/sda1 /media/sda1
```

---

