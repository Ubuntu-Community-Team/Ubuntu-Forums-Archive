---
title: "memory leak?"
date: 2007-02-25
forum: General Help
---

### Post by Salpiche on 2007-02-25
somehow kubuntu is using 494Mb out of 512Mb on idle. What services should I stop in order to recover some memory and avoid performance issues? here is a screen shot.[ATTACH]26138[/ATTACH]

---

### Post by RedSquirrel on 2007-02-25
This is not as bad as you might think. Notice the two entries for buffers and cache? That memory can easily be reclaimed when needed. 

Try (in a terminal):

```
free -m
```

for a better picture of what's going on. Look at the line "-/+ buffers/cache" and under the "used" column.

---

### Post by Salpiche on 2007-02-25
What gets me is that just this morning it was using 246 or so with the remainder free then it got stuck above 400. I did *free -m* a few minutes before taking the screen shot and it went to 300Mb or so then it climbed back to almost 500Mb

---

### Post by RedSquirrel on 2007-02-26
> **Salpiche said:**
> What gets me is that just this morning it was using 246 or so with the remainder free then it got stuck above 400. I did *free -m* a few minutes before taking the screen shot and it went to 300Mb or so then it climbed back to almost 500Mb


You mean 'free -m' reports almost 500 MB ***used***?

Does KDE really gobble up that much memory? This is my 'free -m' with Fluxbox on Xubuntu 6.10 and Firefox running (320 MB RAM):

```

                    total       **used**       free     shared    buffers     cached
Mem:              313       216         96          0         31         82
-/+ buffers/cache:       [COLOR=DarkOrange]**103**[/COLOR]        210
Swap:              627          0        627

```

---

