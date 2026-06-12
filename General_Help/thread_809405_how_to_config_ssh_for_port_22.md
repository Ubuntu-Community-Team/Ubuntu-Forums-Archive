---
title: "how to config ssh for port 22"
date: 2008-05-27
forum: General Help
---

### Post by moonhk on 2008-05-27
Hi All

How to open port 22 for ssh ?

moonhk@hex:~$ ssh moonhk@hex
ssh: connect to host hex port 22: Connection refused
moonhk@hex:~$ 


moonhk

---

### Post by Monicker on 2008-05-27
You need to install the openssh-server package.  After the install it will automatically be started and listening on port 22.

```
sudo apt-get install openssh-server
```

---

