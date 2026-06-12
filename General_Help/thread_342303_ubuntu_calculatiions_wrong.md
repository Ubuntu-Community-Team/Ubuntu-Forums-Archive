---
title: "ubuntu calculatiions wrong?"
date: 2007-01-19
forum: General Help
---

### Post by atlfalcons866 on 2007-01-19
i looked at system monitor and it said no virtual memory was being used but in the 1st picture it shows firefox being used

---

### Post by taurus on 2007-01-19
How about

```
free
```

---

### Post by atlfalcons866 on 2007-01-19
total       used       free     shared    buffers     cached
Mem:        498608     489596       9012          0      30140     226312
-/+ buffers/cache:     233144     265464
Swap:      1453840        192    1453648

does that mean cache is using more?

---

### Post by taurus on 2007-01-19
It means that your swap space is being used a little, the middle value.  If it says 0, then your swap has not being used at all.

---

### Post by Kateikyoushi on 2007-01-19
> **atlfalcons866 said:**
> total       used       free     shared    buffers     cached
Mem:        498608     489596       9012          0      30140     226312
-/+ buffers/cache:     233144     265464
Swap:      1453840        192    1453648

does that mean cache is using more?

It is better to store it in memory if you have free than to swap it out to disc, isn't it ?

---

### Post by atlfalcons866 on 2007-01-19
yes ram is thousands times faster than a disk

---

### Post by Littleweseth on 2007-01-19
Swap usage is not necessarily a bad thing. See here;
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

