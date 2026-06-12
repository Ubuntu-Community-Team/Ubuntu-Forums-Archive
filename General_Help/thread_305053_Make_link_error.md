---
title: "Make link error"
date: 2006-11-22
forum: General Help
---

### Post by Flavian on 2006-11-22
Hi guys!
Every time I want to make a link on a file I get an error!
It says:
> Error "Operation not permitted" while creating a link to "/media/Fat3...enplan.xls".

interesting to note: it works on the Desktop, not anywhere else...
Thanks for any help.
Flo

---

### Post by taurus on 2006-11-22
If you do that from a terminal, you need to include "sudo" in front.  And if you want to use nautilus, then run it with

```
gksudo nautilus
```

---

### Post by CatKiller on 2006-11-22
You can't make a link on a FAT partition. The filesystem doesn't support it.

---

