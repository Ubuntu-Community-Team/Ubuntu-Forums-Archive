---
title: "[SOLVED] Synaptic NOT WORKING!!!"
date: 2008-03-25
forum: General Help
---

### Post by evox on 2008-03-25
Ok so synaptic has been working fine until today when i decide to open it, it gives me an error saying

```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```


So i go to my terminal and when i put that in it says.
```

evox@Ubuntu-Fawn:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
evox@Ubuntu-Fawn:~$ 

```

Really need some help so i can get this system up and running. ive only been a linux user for about 2 days now.

---

### Post by kellemes on 2008-03-25
type:
```
sudo dpkg --configure -a
```

---

### Post by evox on 2008-03-25
> **kellemes said:**
> type:
```
sudo dpkg --configure -a
```

Yea i actually just realized that.
I guess its cause im still new to using command lines even tough i program it doesnt seem like its helped with remembering things like that lol.

---

