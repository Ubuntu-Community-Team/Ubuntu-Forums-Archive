---
title: "Best app to sync files between partitions?"
date: 2007-09-25
forum: General Help
---

### Post by 67GTA on 2007-09-25
I am looking for something to keep my pics, movies, music, docs in sync between linux partitions on the same hard drive without having to manually drag them across. I have seen several ftp or network apps to do this, but is there something to just work across Ubuntu/Kubuntu partitions?

---

### Post by por100pre1 on 2007-09-25
Try Grsync:

```
sudo apt-get install grsync
```

---

### Post by 67GTA on 2007-09-25
Thats perfect. Thanks. I was looking at rsync in the repos, but thought it was only for network syncing. I didn't see grsync. If I can get it set up in cron I will be set.

---

### Post by por100pre1 on 2007-09-25
The Grsync output will show the rsync command used. Once you have Grsync working your way, copy the rsync command and use it on your cron job. :)

---

