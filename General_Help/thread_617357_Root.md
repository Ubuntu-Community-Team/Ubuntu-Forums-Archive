---
title: "Root"
date: 2007-11-19
forum: General Help
---

### Post by henkasdf on 2007-11-19
Hi all,

How do I make a certain user part of the root/administrator group.

Thanks

---

### Post by minus198 on 2007-11-19
Don't know if this works but:

sudo nano /etc/group 

add your username to the end of:

```
root:x:0:
```

So that it becomes:

```
root:x:0:name
```

---

