---
title: "How do I do simple, fast, package name search?"
date: 2013-02-09
forum: General Help
---

### Post by bbalban on 2013-02-09
There used to be sudo aptitude search

There is no search now, using apt-get

There is some apt-cache command which dumps a ton of info

If I search in the Unity top left corner search box, I have to first click applications, and then do search. But then that does not actually search package names.

How do I do simple, reliable, fast, package name search?

Thanks,
Bahadir

---

### Post by Vaphell on 2013-02-09
install aptitude, problem solved ;-)

---

### Post by steeldriver on 2013-02-10
does

```
apt-cache search --names-only *keyword*
```

do what you want?

---

### Post by thermion on 2013-02-10
Or: dpkg -l | grep -i *keyword*

---

### Post by Cheesemill on 2013-02-10
Install aptitude then use...
```
aptitude search foo
```
No need for sudo when using aptitude search.

---

