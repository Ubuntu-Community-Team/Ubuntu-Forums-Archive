---
title: "mounting aufs in /etc/fstab"
date: 2014-02-03
forum: General Help
---

### Post by AmbiguousOutlier on 2014-02-03
Hello, 

I can't figure out how to convert the following line so it works in my fstab?

```
mount -t aufs -o br:/mnt/afs/movies=rw:/mnt/bfs/movies=rw:/mnt/cfs/movies=rw:/mnt/dfs/movies=rw,sum,create=mfs none /mnt/ufs/movies
```


Also on a side note, does fstab mount sequentially or in parallel?

---

