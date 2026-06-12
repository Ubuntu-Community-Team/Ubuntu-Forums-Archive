---
title: "apt-get error: Line 2 too long"
date: 2007-12-11
forum: General Help
---

### Post by calder0n on 2007-12-11
Hey,
Recently apt-get stopped working, I'm not sure when it happened but my damaged hard drive might have something to do with it.

apt-get output:
```
:/etc/apt$ apt-get
E: Line 2 too long (max 1024)

```

Now, I've looked for long strings in /etc/apt/ but nothing seems to be out of the ordinary.

```

-rw-r--r-- 1 root root    0 2007-12-05 13:08 apt.conf
drwxr-xr-x 2 root root 4096 2007-12-11 16:24 apt.conf.d
-rw------- 1 root root    0 2007-04-15 04:49 secring.gpg
-rw-r--r-- 1 root root 2390 2007-11-04 13:04 sources.list
drwxr-xr-x 2 root root 4096 2007-10-15 22:11 sources.list.d
-rw------- 1 root root 1200 2007-11-04 12:29 trustdb.gpg
-rw-r--r-- 1 root root 6760 2007-11-04 12:29 trusted.gpg

```

Any other ideas? 

Thanks

---

### Post by aysiu on 2007-12-11
I don't think *apt-get* can work by itself.

Try something like ```
sudo apt-get update
``` You may also want to post your /etc/apt/sources.list file here.

---

### Post by calder0n on 2007-12-11
UPDATE: I finally got it working again by moving the contents of /etc/apt/apt.conf.d to a temp directory.

Now, what are these files for? Can I just remove them? Everthing seems to be working again. 

Thanks.

---

