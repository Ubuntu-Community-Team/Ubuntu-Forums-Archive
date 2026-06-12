---
title: "automatix"
date: 2007-04-03
forum: General Help
---

### Post by garymc1 on 2007-04-03
how can i uninstall automatix using terminal ??

---

### Post by sisco311 on 2007-04-03
```
sudo apt-get remove automatix2
```

---

### Post by Waappu on 2007-04-03
Hi

Type in terminal```
sudo aptitude remove --purge-unused automatix2
rm ~/.automatix
```

And you must remove Automatix ropositorys manualy from sources.list

---

### Post by garymc1 on 2007-04-03
how do i edit the  sources.list
thanks gary

---

### Post by taurus on 2007-04-03
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

