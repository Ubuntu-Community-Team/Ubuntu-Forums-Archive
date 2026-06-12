---
title: "Apache Install"
date: 2008-02-05
forum: General Help
---

### Post by MeTaLliC on 2008-02-05
Hi There,

I'm having the following issues with installing Apache. Below is the apt-get message.

> user@dev:~$ sudo apt-get install apache2
[sudo] password for user:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package apache2 has no installation candidate


Anyone have any idea's? This was working the other night, but not today (had to create a new VM).

---

### Post by jan quark on 2008-02-05
try this version
```
sudo apt-get install apache2.2-common
```

---

