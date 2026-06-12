---
title: "free or superkaramba who to belive"
date: 2006-11-19
forum: General Help
---

### Post by zapcojake on 2006-11-19
Hello, superkaramba says I'm only using 248mb of 440 mb system memory but the results of free > memuse are
jake@kubuntu:~$ free > memuse
jake@kubuntu:~$ cat memuse
             total       used       free     shared    buffers     cached
Mem:        450736     444940       5796          0       6948     206300
-/+ buffers/cache:     231692     219044
Swap:            0          0          0
jake@kubuntu:~$
whom do I believe and what do I do to get them both reporting the same?

For the newbs issuing the free command reports memory usage on your system The > is a pipe so free > memuse means pipe the output of free to a file called memuse.

---

