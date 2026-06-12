---
title: "How to remove orphaned packages"
date: 2017-04-03
forum: General Help
---

### Post by bonestabone on 2017-04-03
I'm trying to find all orphaned packages on my system, i.e. packages that were pulled in as dependencies for another package that I later removed.

I know in Debian there is deborphan but is this the preferred way in Ubuntu? Thanks.

---

### Post by QIII on 2017-04-03
Hello!

```
sudo apt autoremove 
```

or

```
sudo apt-get autoremove 
```

(as appropriate) should work for anything you have installed from the repos or (generally) via debs.

---

### Post by bonestabone on 2017-04-03
Hey thanks for that reply, I know about autoremove but I thought it didn't pick up all orphaned packages in some cases.

---

### Post by deadflowr on 2017-04-03
deborphan is installable if you prefer it.

---

### Post by bonestabone on 2017-04-03
I noticed also there's a front-end for deborphan, gtkorphan

---

