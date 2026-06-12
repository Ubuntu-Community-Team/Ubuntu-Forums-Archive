---
title: "How to change root permission"
date: 2015-02-14
forum: General Help
---

### Post by vidura2 on 2015-02-14
I had some video files and those are deleted by mistaken. But after I was recover those files using testdisk 6.14-3. Now i want to delete those file. But it says I haven't permission to delete it. How can I delete those files??
Thnks.

---

### Post by carl4926 on 2015-02-14
chown the file or the entire directory

---

### Post by Bucky Ball on 2015-02-15
*Thread moved to **General Help**.*

I'm presuming you are using Ubuntu. Open a terminal and:

```
gksudo nautilus
```

This will open the file manager as root. Delete the files. DON'T do anything else as you are root and can cause some real damage. Once files are deleted, close the file manager.

---

