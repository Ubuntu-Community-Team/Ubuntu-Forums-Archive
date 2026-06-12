---
title: "folder with lock icon?"
date: 2008-06-13
forum: General Help
---

### Post by searayman on 2008-06-13
I have a folder with a lock icon on it, and it has a buch of images I can not take out of it, because it is locked.

How can i unlock this folder via terminal?

---

### Post by drs305 on 2008-06-13
You have to change ownership:
```
sudo chown -R username:username /path/folder
```

Alternatively, you can view and access the folder by opening nautilus as root:
```
gksudo nautilius
```

---

### Post by searayman on 2008-06-13
istead of path tpo folder can i just put the folders name if i have cd'ed to the directory the folder is in?

---

### Post by drs305 on 2008-06-13
> **searayman said:**
> istead of path tpo folder can i just put the folders name if i have cd'ed to the directory the folder is in?

Yes, you can do that.

---

