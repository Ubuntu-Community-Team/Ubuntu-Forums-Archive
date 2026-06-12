---
title: "How do I gain file permissions in 15.04?"
date: 2015-05-31
forum: General Help
---

### Post by kim15 on 2015-05-31
I am trying to add a new GTK theme but I need to move the folder to usr/share/themes and it won't let me because it says I don't have permission.  I tried running sudo su in the terminal, but that didn't help at all.  How can I do this?

---

### Post by QDR06VV9 on 2015-05-31
use gksudo then your file manger
for an example, for gnome "gksudo nautilus" with out the quotes

---

### Post by Frogs Hair on 2015-05-31
The package gksu is no longer installed by default, but is a dependency of some programs . If the command fails install gksu.
```
sudo apt-get install gksu 
```

---

### Post by kim15 on 2015-05-31
> **runrickus said:**
> use gksudo then your file manger
for an example, for gnome "gksudo nautilus" with out the quotes

Thanks!  That totally worked!

---

