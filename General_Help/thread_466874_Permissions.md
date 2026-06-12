---
title: "Permissions"
date: 2007-06-07
forum: General Help
---

### Post by watt0 on 2007-06-07
Is there any way to disable permissions?

---

### Post by joselin on 2007-06-07
Sure. But, could you explaint it a little more.

---

### Post by watt0 on 2007-06-07
some of the files in my home folder have changed ownership to root for some reason, and I don't want to have to go through and change everything back.

---

### Post by gerscht on 2007-06-07
they have probably changed to root, as you've created them as root ;)
you can revert all of them by
```

sudo chown USERNAME:USERNAME /home/USERNAME/* -R

```
(the -R option has to be capital)

---

### Post by watt0 on 2007-06-07
Thanks!

---

