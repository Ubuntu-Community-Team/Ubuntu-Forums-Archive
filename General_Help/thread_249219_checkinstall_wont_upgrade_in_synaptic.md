---
title: "checkinstall wont upgrade in synaptic"
date: 2006-09-02
forum: General Help
---

### Post by nix4me on 2006-09-02
My synaptic shows checkinstall having an upgrade but when mark all upgrades is selected, checkinstall is not selected.

Anyone else have this problem?

nix4me

---

### Post by patwack on 2006-09-02
yep, along with totem, don't know why

---

### Post by ayoli on 2006-09-02
you may try in a terminal
```
sudo aptitude update && sudo aptitude dist-upgrade
```
btw, there is a dependancies problem, aptitude should upgrade your packages, but will removing the ones that cause dep problem.
regards.

---

### Post by bluevoodoo1 on 2006-09-09
> **ayoli said:**
> you may try in a terminal
```
sudo aptitude update && sudo aptitude dist-upgrade
```



Awesome. Haven't had to use aptitiude yet... This seems to have solved the issue for me.

---

