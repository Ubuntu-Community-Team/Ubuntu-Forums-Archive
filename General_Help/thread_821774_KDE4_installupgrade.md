---
title: "KDE4 install/upgrade"
date: 2008-06-07
forum: General Help
---

### Post by ricardisimo on 2008-06-07
Do I just select the KDE4 package in Add/Remove if I want to try out the new desktop enviro? If I don't like it, how do I "downgrade"? Thanks in advance.

---

### Post by Happy_Man on 2008-06-07
If you want the KDE 4 desktop, open a terminal and type ```
sudo aptitude install kubuntu-kde4-desktop
```. And if you want to remove it, type ```
sudo aptitude remove kubuntu-kde4-desktop
```.

---

### Post by ricardisimo on 2008-06-07
Thank you. Now, if I don't like it, and I remove it with aptitude, does it reinstall the previous DE? Or is KDE4 just a "top layer" that can be added and removed at will without disturbing anything else?

---

### Post by Happy_Man on 2008-06-07
It will only remove the KDE4 desktop it installed with the first command, so GNOME, KDE3, etc. will all be fine.

---

### Post by ricardisimo on 2008-06-07
Thanks again! I take back all those things I said about you before.

---

