---
title: "remove icons for uninstalled apps"
date: 2019-09-11
forum: General Help
---

### Post by jackdoom on 2019-09-11
hi, linux noob here!! i just uninstalled a few programs which i ran using wine4.0 but the icons are still showing in all applications. How do i remove those?? 
PS: sorry in advance if i posted this somewhere wrong or if such a thread already exists. and thank you for help as well!! :D

---

### Post by Dev'olution on 2019-09-11
There used to be an app called alacarte - not sure if it's still around - that can be used to handle this.

Install via terminal:

```
sudo apt-get install alacarte
```

---

### Post by CatKiller on 2019-09-11
The menu entries are just text files. They're in ~/.local/share/applications.

---

