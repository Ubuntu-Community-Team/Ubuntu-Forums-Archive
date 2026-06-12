---
title: "[SOLVED] How do I figure out what edition I have?"
date: 2008-01-03
forum: General Help
---

### Post by amdalex on 2008-01-03
I installed Ubuntu a while ago on my computer but I forget whether it was edgy eft or fiesty fawn. How can I tell? thanks

---

### Post by rfruth on 2008-01-03
System >> about Ubuntu :confused:

---

### Post by p_quarles on 2008-01-03
Type this in a terminal:
```
cat /etc/issue
```

---

### Post by kebes on 2008-01-03
There may be a better way, but a simple way is to just open the file "/etc/apt/sources.list" and see what the repositories are set to (dapper, edgy, feisty, gutsy, ...):

```

cat /etc/apt/sources.list

```

---

### Post by zvacet on 2008-01-03
```
lsb_release -a
```

---

### Post by amdalex on 2008-01-03
thanks

---

### Post by ~LoKe on 2008-01-03
```
lsb_release -a
```
Nice, I can use this in the script that I "borrowed" from an Arch user.

---

