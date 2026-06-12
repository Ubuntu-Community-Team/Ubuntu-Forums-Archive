---
title: "How to uninstall programs using the console"
date: 2008-05-02
forum: General Help
---

### Post by blacappuccino on 2008-05-02
Hey guys is possible to uninstall applications with console... I installed privoxy using a .deb file and i want to uninstall but in the Add/Remove programs i didn't find...

So can u explain me with details how to uninstall it, like when we want to install we type, if the application is called "tor":

> sudo apt-get install tor

Cheers

---

### Post by Monicker on 2008-05-02
```
sudo apt-get remove tor
sudo apt-get --purge remove tor
```

The second line also removes configuration files, whereas the first does not.

---

### Post by blacappuccino on 2008-05-02
thanks a lot Monicker

---

