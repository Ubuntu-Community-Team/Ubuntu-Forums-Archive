---
title: "change sources.list.d and sources.list location"
date: 2016-10-10
forum: General Help
---

### Post by mintmag on 2016-10-10
Hi there guys. So I wish to change the default location of the  sources.list.d and sources.list location to a mounted hard drive. I created a file in apt.conf.d with ```
dir::etc::sourcelist path/to/new/sources.list 
``` and ```
dir::etc::sourceparts path/to/new/sources.list.d 
```

However the system ignores these settings and still uses the default location.

---

### Post by TheFu on 2016-10-10
If you mount the new storage over /etc/apt/ it will work.  Or you can use symbolic links (ugly).  Never tried or heard of anyone trying to do what you described or with the mount I suggest.  May I ask why?  Chances are there could be a more maintainable way to achieve the desired end-goal.  Perhaps?

---

### Post by jeremy31 on 2016-10-10
mintmag

If this also concerns Linux Mint it should have been posted in the Mint subforum

---

