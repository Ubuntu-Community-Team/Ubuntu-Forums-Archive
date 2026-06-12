---
title: "somethink really strange with ram usage in kubuntu hardy"
date: 2008-07-01
forum: General Help
---

### Post by syms on 2008-07-01
[IMG]http://img26.picoodle.com/img/img26/4/7/1/f_snapshot3m_325050a.png[/IMG]

look, ksysguard shows that there is only 60 m free, but conky shows that it is only 34% ram used. in what program i have to believe? which program shows right ram usage?

---

### Post by hyper_ch on 2008-07-01
run
```

free -m

```

---

### Post by BlueSkyNIS on 2008-07-01
They are both right. Look at the blue graph in ksysguard (just above 106844 line), that's application memory usage and that's what conky is reporting (109.13 MiB).

---

### Post by syms on 2008-07-01
> **hyper_ch said:**
> run
```

free -m

```

here:

fsimas@simas-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           313        308          4          0          6        159
-/+ buffers/cache:        142        170
Swap:          407         21        386

it shows that there is 4 free megabytes, but then why there is only 21 mb used for swap? if there could be only four megabytes free then swap partition will be used ~308 mb.

---

### Post by sdennie on 2008-07-01
In the free -m line, the interesting numbers are on the second row.  Linux caches files so, it's very, very common to show something approaching 0M free of memory if you include the cache.  The second line shows memory usage if the cache isn't included which is more accurate because that memory can easily be discarded at any time to make room for your applications if needed.  Everything looks normal to me.

---

### Post by syms on 2008-07-01
> **BlueSkyNIS said:**
> They are both right. Look at the blue graph in ksysguard (just above 106844 line), that's application memory usage and that's what conky is reporting (109.13 MiB).
maybe this sounds noobish, but then what means yellow graph? :D

---

### Post by hyper_ch on 2008-07-01
looks to me like the blue graph is the actual ram used and the blue one is the cache... you know, unused ram is wasted ram ;)

and when you post next time something as result from a command, embrace it with [noparse]```

```[/noparse] brackets... then it keeps it's format and makes it easier to read.

---

### Post by syms on 2008-07-01
thanks :D ! so you say that it is normal that i have only four megabytes left :KS

---

### Post by sdennie on 2008-07-01
> **syms said:**
> thanks :D ! so you say that it is normal that i have only four megabytes left :KS

Yes, the longer you use your machine, the more things will get cached.  It doesn't matter if you have 256M of memory or 4G of memory, eventually, you are likely to be at the point where apps + cache takes all your memory.  This is a good thing as it avoids reading the disks for cached information and so makes the system much faster for many operations.  If your apps need that cached memory it will be dropped in favor of your apps so, it's essentially free memory but, as hyper_ch said, "unused memory is wasted memory".

---

### Post by BlueSkyNIS on 2008-07-01
> **syms said:**
> maybe this sounds noobish, but then what means yellow graph? :D

I'm not sure but you can hover your mouse over a graph and a color legend will pop up, so you can see what colors represent.

---

