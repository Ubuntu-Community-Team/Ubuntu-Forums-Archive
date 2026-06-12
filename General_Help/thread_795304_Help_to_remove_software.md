---
title: "Help to remove software"
date: 2008-05-15
forum: General Help
---

### Post by TobbeQ on 2008-05-15
Hi was wondering how I uninstall a software that I've installed with GDebi.

Thx in advance.

---

### Post by latna on 2008-05-15
I'm pretty sure it should show up in synaptic, so you should be able to uninstall it just like any other program.

---

### Post by strabes on 2008-05-15
In a terminal (Applications > Accessories > Terminal): ```
sudo aptitude uninstall packagename
```

If you're unsure of the package's name, you can type in the first few characters (i.e. "fire" for firefox) and then hit tab a few times and it will display the packages that begin with those characters.

---

