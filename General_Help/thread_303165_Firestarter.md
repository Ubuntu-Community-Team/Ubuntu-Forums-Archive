---
title: "Firestarter"
date: 2006-11-19
forum: General Help
---

### Post by Ptah on 2006-11-19
I am looking for firestarter, I went into synaptic and typed in firestarter but no luck.  I even typed in firewall but only came up with shorwall.  I thought that firestarter is in the ubuntu repros.

---

### Post by taurus on 2006-11-19
You need to enable both universe & multiverse in your /etc/apt/sources.list.  You can do that by removing the # in front of those lines...

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude install firestarter
```

---

