---
title: "How to find out which process uses which files"
date: 2006-08-13
forum: General Help
---

### Post by jazzgossen on 2006-08-13
Is there a way to find out which processes accesses which files. For example, sometimes I can't unmount a file system because it is "busy". Then I'd like to know which process is responsible for that.

---

### Post by jordilin on 2006-08-13
Yes, type
```
fuser filename
```

---

