---
title: "Add web repos with aptitude in terminal"
date: 2008-03-20
forum: General Help
---

### Post by Raccoon1400 on 2008-03-20
How do I add the ubuntu internet repos in aptitude?
Now it only uses the software on the disk.
At the moment, I don't have use of a gui.

---

### Post by pointone on 2008-03-21
Edit /etc/apt/sources.list and uncomment the repositories you want access to, then run "aptitude update" or "apt-get update".

---

### Post by Raccoon1400 on 2008-03-21
The CD is the only one that shows up.
I now have a gui.(fluxbox)

---

### Post by aysiu on 2008-03-21
> **Raccoon1400 said:**
> The CD is the only one that shows up.
I now have a gui.(fluxbox)
Try [these instructions](http://www.psychocats.net/ubuntu/sources#key).

---

