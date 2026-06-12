---
title: "General apt-get/libraries question"
date: 2007-12-11
forum: General Help
---

### Post by roody on 2007-12-11
Hi
I need to install the necessary libraries for nomachine.
so I tried this:

root@Schoko:/home/roderick# apt-get install libstdc++2.10-glibc2.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstdc++2.10-glibc2.2

thank you for your help....

---

### Post by kpkeerthi on 2007-12-11
Try from synaptic. Use the search option and search for 
```
libstdc++
```
and 
```
glibc
```

---

### Post by roody on 2007-12-11
> **kpkeerthi said:**
> Try from synaptic. Use the search option and search for 
```
libstdc++
```
and 
```
glibc
```

I found the libstdc++6 library installed

and only glibc.doc ( I suppose this is not the library to install)

---

### Post by roody on 2007-12-15
works, thx!

---

