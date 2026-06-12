---
title: "having root problems"
date: 2008-01-13
forum: General Help
---

### Post by dzuari on 2008-01-13
i am trying to give a file permission to all my accounts but the owner is set as:root.  how do i login or change this file, i cant login as root at the ubuntu start up... im a newb...sry...

---

### Post by PmDematagoda on 2008-01-13
Open Nautilus in root mode using:-
```
sudo nautilus
```

That will allow you to make the necessary permissions changes.

---

### Post by articpenguin on 2008-01-13
sudo is for terminal applications. Use gksu for graphical applications like natilus.

> gksudo nautilus


[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by PmDematagoda on 2008-01-13
I tried opening Nautilus using gksudo but it did not work for some reason, sudo on the other hand works well.

---

