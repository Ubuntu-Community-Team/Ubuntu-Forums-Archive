---
title: "how can i log into root?"
date: 2006-09-18
forum: General Help
---

### Post by eighthate on 2006-09-18
thanks

---

### Post by src2206 on 2006-09-18
As username type "root".
Then in the corresponding password field type tyheroot password and then enter.
Voala! yo're root :D

---

### Post by PriceChild on 2006-09-18
You may use:

sudo <<non graphical app>>
e.g. sudo aptitude

gksudo <<graphical app>>
e.g. gksudo synaptic

sudo su
to gain a root terminal

---

### Post by aysiu on 2006-09-18
You don't log into root.

If you're using the terminal, preface your command with the word *sudo*.

If you want to make point-and-click changes, press Alt-F2 and type (or create a launcher for the command) ```
gksudo nautilus
``` That's for Ubuntu. If you're using Kubuntu, the command you want is ```
kdesu konqueror
```

---

### Post by Ramses de Norre on 2006-09-18
You might want to read [this](http://wiki.ubuntu.com/RootSudo).

---

### Post by eighthate on 2006-09-18
thanks everyone.

---

