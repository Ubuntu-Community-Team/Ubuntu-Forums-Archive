---
title: "grsync &amp; .gvfs"
date: 2016-10-05
forum: General Help
---

### Post by cmcanulty on 2016-10-05
i have read many posts about gvfs causing grsync to fail but whatever exclude path I put for it doesn't work. I am backing up /home to an external hard drive and trying to exclude ./gvfs.I have tried every way I can think of to do the path correctly but none work.What is the correct path? It is weird as .gvfs is in /home but root owns it and won't let me change ownership 

```
--exclude /.gvfs
```

---

