---
title: "Finding a text string in all files???"
date: 2013-10-12
forum: General Help
---

### Post by Bobby_James on 2013-10-12
Let's say I have in a text file the characters "Yes, my name is Bobby!!!"

How would I search for that string among all files on one hard drive?

I have played around with grep and find to no avail.

Thanks!

---

### Post by howefield on 2013-10-12
Try something like

```
grep -irI "Yes, my name is Bobby!!!" /pathtofiles
```

---

