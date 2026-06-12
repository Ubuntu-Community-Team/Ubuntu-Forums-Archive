---
title: "gnome will only go to splash screen"
date: 2007-01-12
forum: General Help
---

### Post by djsamsel on 2007-01-12
i can boot into kde, or gnome fail-safe but when when i try regular gnome it only goes to the splash screen. i've tried updating everything. i tried deleting .gnome and .gnome2 in my home folder but nothing changes. any suggestions? thanks, dj

---

### Post by netadptr0719 on 2007-01-12
Have you tried going into the terminal boot and reinstalling gnome?
```

sudo apt-get remove gnome-base
sudo apt-get install gnome-base
```
I had a problem with gnome once and that fixed it.

---

