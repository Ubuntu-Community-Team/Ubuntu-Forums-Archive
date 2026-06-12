---
title: "Gnome-core installed but terminal wanted on startup"
date: 2006-11-02
forum: General Help
---

### Post by MrMattles on 2006-11-02
Hi there,

After a little advice, I have installed edgy server and then installed gnome-core. I want gnome on the machine however I dont want it at start up. I would much rather just type "startx" when I want a GUI......
how can I turn off the automatic start up of gnome?

Thanks
MrMattles8) 8)

---

### Post by Ramses de Norre on 2006-11-02
```
sudo aptitude install sysv-rc-conf
sudo sysv-rc-conf
```
Scroll down to "gdm" and remove the X in column 2 with the space bar, then press 'q'.
Gdm wont start on startup no more.

---

