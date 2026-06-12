---
title: "Quick partition question"
date: 2007-04-04
forum: General Help
---

### Post by burritomaster on 2007-04-04
I want to reszie my linux partition. Do I have to boot into a live CD, unmount my Linux partition "donor" partion. Then just resize them as I did during installation.  Will this corrupt anything. Thanks in advanced.

---

### Post by m.musashi on 2007-04-04
From a live CD you can run
```
sudo gparted
```
and make changes. I don't believe your partitions will be mounted but if so you will have to unmount them first.

In theory this should not affect your data but in reality it can. I just did this a couple days ago and gparted failed during the process and I lost my /home. Fortunately every thing I consider important was backed up. You should do the same just in case. However, if all goes well you should not lose anything.

---

