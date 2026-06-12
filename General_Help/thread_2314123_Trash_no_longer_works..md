---
title: "Trash no longer works."
date: 2016-02-18
forum: General Help
---

### Post by Evil Wayz on 2016-02-18
After my last update, Trash can doesn't work.  I can open it, but the restore and empty buttons are grayed out.  I can delete things  by right clikcing on them, but if I want to restore a file accidentally trashed, I can't.  ANyone have any ideas on this?

---

### Post by ajgreeny on 2016-02-18
In terminal please run command ```
ls -la .local/share/Trash/
``` and show us the output in code tags, which will tell us the ownership and permissions of that folder and its subfolders.

---

### Post by Evil Wayz on 2016-02-21
> **ajgreeny said:**
> In terminal please run command ```
ls -la .local/share/Trash/
``` and show us the output in code tags, which will tell us the ownership and permissions of that folder and its subfolders.


Output:
```
wolf@shaitan:~$ ls -la .local/share/Trash/
total 1296
drwx------  5 wolf wolf   4096 Dec  5  2014 .
drwxr-xr-x 39 wolf wolf   4096 Feb 21 15:52 ..
drwx------  2 wolf wolf   4096 Feb 21 15:52 expunged
drwx------  2 wolf wolf 565248 Feb 21 15:52 files
drwx------  2 wolf wolf 741376 Feb 21 15:52 info

```

---

