---
title: "Keyboard up key in terminal"
date: 2013-06-04
forum: General Help
---

### Post by intelaravind on 2013-06-04
Hi,

In the gnome terminal when I press the up key, it shows the last executed command. But not the last different executed command. How can I make up key to do this. I am using ubuntu 13.04

eg: consider the sequence

1. ps
2. ls
3. ls

up key one time gives ls (this is fine). Next time again it gives ls (I want ps here).

Regards

---

### Post by Cheesemill on 2013-06-04
Edit your ~/.bashrc file and add the following line...
```
HISTCONTROL="erasedups"
```

---

