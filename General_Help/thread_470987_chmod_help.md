---
title: "chmod help"
date: 2007-06-11
forum: General Help
---

### Post by nami on 2007-06-11
I am having difficulty accessing files i have which i created on another computer.  How do I give myself access to these files now that i no longer have access to the original computer?

> nami@nami-desktop:/media/backup$ ls -l
total 17681232
-rw------- 1 root root 2136002229 2007-06-09 20:41 backup.000
-rw------- 1 root root 2135946880 2007-06-09 20:43 backup.001
-rw------- 1 root root 2135946880 2007-06-09 20:44 backup.002
-rw------- 1 root root 2135955088 2007-06-09 20:46 backup.003
-rw------- 1 root root 2135938672 2007-06-09 20:47 backup.004
-rw------- 1 root root 2135946880 2007-06-09 20:48 backup.005
-rw------- 1 root root 2135946880 2007-06-09 20:49 backup.006
-rw------- 1 root root 2135946880 2007-06-09 20:50 backup.007
-rw------- 1 root root 1000188848 2007-06-09 20:51 backup.008
drwx------ 2 root root      16384 2007-06-09 20:28 lost+found
nami@nami-desktop:/media/backup$

---

### Post by rscott5 on 2007-06-11
This should do the trick:

```
chown -R nami /media/backup
```

That will change file ownership for the /media/backup directory and everything to inside to the nami user. Replace nami if you want to use a different user.

---

### Post by nami on 2007-06-11
i made this from a live cd so if i apply the above change, will i be able to use these films from the live cd?

---

### Post by stchman on 2007-06-11
> **rscott5 said:**
> This should do the trick:

```
chown -R nami /media/backup
```

That will change file ownership for the /media/backup directory and everything to inside to the nami user. Replace nami if you want to use a different user.

You need sudo in front of that chown.  Try this:

sudo chown -R nami:nami /media/backup
sudo chmod -R 755 /media/backup

This should do the trick.  Of course replace nami with the user you wish to have access to the files.

---

### Post by nami on 2007-06-11
instead of making me the owner, is it possible to make everyone and everything have access to the files?

---

### Post by taurus on 2007-06-11
```
sudo chmod -R 777 /media/backup
```

---

