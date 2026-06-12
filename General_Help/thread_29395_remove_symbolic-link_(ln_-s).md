---
title: "remove symbolic-link (ln -s)"
date: 2005-04-24
forum: General Help
---

### Post by RedFox03 on 2005-04-24
Does anyone know how to remove a symbolic link?

I just want to undo the step:

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1



thx,

---

### Post by heimo on 2005-04-24
Just the same way as you would remove any other file:
 ```
sudo rm /usr/lib/libesd.so.1
```

---

