---
title: "strange problem with swap"
date: 2007-02-28
forum: General Help
---

### Post by MkfIbK7a on 2007-02-28
well the problem is really that i dont have any here is my free -m

```
jon@albert:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           376        355         20          0          7        176
-/+ buffers/cache:        172        204
**_Swap:            0          0          0_**
jon@albert:~$ 

```

no swap so how can i make some?

EDIT: ok i had a swap partition but it wasnt activated so i edited fstab and did a swapon -a now everythings fine

---

