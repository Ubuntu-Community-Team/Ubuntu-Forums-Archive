---
title: "Questions about ps"
date: 2008-04-16
forum: General Help
---

### Post by Dudsmacka2 on 2008-04-16
If I use a command, such as:

```
ps -p 6341 u
```

Among the results, it returns the cpu %.  If I have a multi-core system (be it a core2 or a quad core) is that the percentage of one core or all the cores?

---

### Post by ghostdog74 on 2008-04-16
you can use mpstat

---

### Post by BaffledMollusc on 2008-04-16
You can also use the "top" command. The "%CPU" column lists how much of your CPU is being used by that process. If you have a single-core CPU, the most it can add up to is 100%. If you have, say four cores, the maximum the total will add up to is 400%. 

So, for example, if you had a quad core CPU and were running four separate processes and each was CPU bound, you'd see four processes at 100% returned by top.

---

