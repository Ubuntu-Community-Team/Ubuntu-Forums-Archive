---
title: "Disable Gnome"
date: 2007-04-28
forum: General Help
---

### Post by dgcarter on 2007-04-28
I am using Ubuntu 6.06 Desktop as my server and i want to disable Gnome on startup with out completely removing it. Just to increase performance. then i want to be able to get it up again by entering startx or something like that.

How do i do this?

---

### Post by dgcarter on 2007-04-28
anyone???

---

### Post by zvacet on 2007-04-28
```
sudo /etc/init.d/gdm stop
```

---

