---
title: "PAE Lubuntu"
date: 2019-05-10
forum: General Help
---

### Post by zacmitche11 on 2019-05-10
Is PAE standardly turned on with Lubuntu,  or do I need to enable it somehow? If so can someone explain how to do so?

---

### Post by Xian on 2019-05-10
Lubuntu supported releases use a PAE-enabled kernel as the default  --- nothing to enable.

---

### Post by zacmitche11 on 2019-05-10
Cool thanks. I wonder why I can only see 3gb of my 4gb of ram then, I'm using 64 bit.

---

### Post by Xian on 2019-05-10
Post the output of this terminal command:

```
free -m
```

---

### Post by zacmitche11 on 2019-05-11
total        used        free      shared  buff/cache   available
Mem:           2991         825         837          80        1328        1925
Swap:           975           0         975

---

### Post by Topsiho on 2019-05-12
Possibly about 1 gb is used by the videocard.
Topsiho

---

