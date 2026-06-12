---
title: "Deleted xorg.conf @ my desktop box .."
date: 2007-05-28
forum: General Help
---

### Post by loathsome on 2007-05-28
.. What do I do to restore it? =/

---

### Post by taurus on 2007-05-28
You need to generate a new one with

```
sudo dpkg-reconfigure xserver-xorg
```
However, there may be a backup copy of it in /etc/X11.

```
ls -la /etc/X11
```

---

### Post by loathsome on 2007-05-28
No, there's no backup.

Thank you, I'll try to create a new! :D

---

### Post by loathsome on 2007-05-28
Thanks a lot, worked flawlessly!!

---

