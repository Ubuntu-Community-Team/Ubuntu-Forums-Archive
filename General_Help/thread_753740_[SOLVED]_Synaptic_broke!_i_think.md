---
title: "[SOLVED] Synaptic broke! i think?"
date: 2008-04-13
forum: General Help
---

### Post by mjp216 on 2008-04-13
help, i dont know anything about the situation.
[IMG]http://i58.photobucket.com/albums/g250/mike_post/Screenshot-synaptic.png[/IMG]

---

### Post by 1/0 on 2008-04-13
First check that duplicate in /etc/apt/sources.list

If that doesn't help try:

```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by mjp216 on 2008-04-13
i have :
sources.list
sources.list.backup
sources.list.distUpGrade
sources.list.save

idk if those are considered duplicates?

---

### Post by 1/0 on 2008-04-13
check inside the file.

```
sudo nano /etc/apt/sources.list
```

look for that hardy/partner line and try adding # in front of it. (ctrl) + (x) to exit and press y to save).

---

### Post by mjp216 on 2008-04-13
i just removedthe sources cuz they werent important, it was just opera and i dont use it, so thanks anyway

---

### Post by 1/0 on 2008-04-13
Glad to help!

---

