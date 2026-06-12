---
title: "help on synaptic"
date: 2006-11-17
forum: General Help
---

### Post by Colherdepau on 2006-11-17
i got the following error while trying to install 
libglu1-mesa-dev:
  Depends: libglu1-mesa (=6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 will be installed

can anyone help?

---

### Post by taurus on 2006-11-17
> **Colherdepau said:**
> i got the following error while trying to install 
libglu1-mesa-dev:
  Depends: libglu1-mesa (=6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 will be installed

can anyone help?
From the title of your thread, I guess you try to install linglu1-mesa-dev using synaptic!  What happens if you run it from a terminal, Applications -> Accessories -> Terminal,

```
sudo aptitude update
sudo aptitude install libglu1-mesa-dev
```
Otherwise, paste your /etc/apt/sources.list here then.

```
cat /etc/apt/sources.list
```

---

### Post by jhenager on 2006-11-17
> **Colherdepau said:**
> i got the following error while trying to install 
libglu1-mesa-dev:
  Depends: libglu1-mesa (=6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 will be installed

can anyone help?

Synaptic checks for dependencies and asks you if it is ok to install another file that is needed. You can just ok it, and it should run fine.

---

