---
title: "Partition size"
date: 2013-08-19
forum: General Help
---

### Post by emerson1979 on 2013-08-19
Hello Everyone
                     I'd like to get some advice on the sizes of the linux partitions. Specifically what size partitions for boot and root.


Thank You

---

### Post by carl4926 on 2013-08-19
/boot not necessary

/ (root) 20 - 30 GB
/home as big as you can make it 100GB ..whatever

But actually Ubuntu defaults to just / (root) no separate /home
In which case just have / and make it big

---

### Post by rnerwein2 on 2013-08-19
> **emerson1979 said:**
> Hello Everyone
                     I'd like to get some advice on the sizes of the linux partitions. Specifically what size partitions for boot and root.


Thank You
hi
in my experince (30 years unix) i am satisfied with the following partitionig (but at least it depends on the size of your disk(s):
/  (including boot but nor /var) 30 GB
/var 50 GB (a lot of stuff is collected in /var)
/home 60 GB ( it depends on how many users you have may be bigger)
/data as big as you can but with subdirectories (music, games, blablu etc. )
and give an exchangeable disk (it's) cheep a change. easy to run a backup with e.g. rsync or so. the time will come and you will be happy to get it !
by the side - they lost my profile (or i can't find it after the last chaos here).
why a couple of partitions: if you have a new installation - you ain't loose all your data - it's just easier to handle.
!!!---> this partitioning need a big accountability on the administration side (and i think that's you).
have fun with your system - all this approchements are just for a hint
ciao
ups this is double - delete the first one. my net was gone

---

