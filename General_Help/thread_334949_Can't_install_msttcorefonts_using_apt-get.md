---
title: "Can't install msttcorefonts using apt-get"
date: 2007-01-09
forum: General Help
---

### Post by chapterthree on 2007-01-09
Hi All,

I'm using Ubuntu 6.10.

```
user@hostname:/etc$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate
user@hostname:/etc$
```

Any ideas?

---

### Post by meng on 2007-01-09
Have you enabled multiverse repositories?
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by chapterthree on 2007-01-09
> **meng said:**
> Have you enabled multiverse repositories?
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Oh, yeah that'll do it :)  I had everything else enabled, but forgot to add multiverse.  Thanks!

---

