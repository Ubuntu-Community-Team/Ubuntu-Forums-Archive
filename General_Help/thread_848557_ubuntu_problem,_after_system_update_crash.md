---
title: "ubuntu problem, after system update crash"
date: 2008-07-03
forum: General Help
---

### Post by meloco on 2008-07-03
Hi,

Every time i try to access the system update, or Synaptic Package Manager this error appears:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I'm sorry if this has been asked a thousand times, but it's my first time using Ubuntu.

Many thanks for all the help,

Meloco

---

### Post by Elfy on 2008-07-03
Yes it has been asked a thousand times by a thousand first time users :D the answer is in the message - open a terminal from accessories and paste this in then enter - enter password it will be blank, but it is there.

```
sudo dpkg --configure -a
```

---

### Post by gator64 on 2008-07-03
You could try going into Applications-->Accessories-->Terminal and at the prompt entering:

```
dpkg --configure -a
```

---

### Post by Elfy on 2008-07-03
> **gator64 said:**
> You could try going into Applications-->Accessories-->Terminal and at the prompt entering:

```
dpkg --configure -a
```
except the op would get the superuser message

---

