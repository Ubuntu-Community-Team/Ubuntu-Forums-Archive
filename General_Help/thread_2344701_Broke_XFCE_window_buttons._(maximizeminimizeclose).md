---
title: "Broke XFCE window buttons. (maximize/minimize/close)"
date: 2016-11-27
forum: General Help
---

### Post by gabers2004 on 2016-11-27
Hello! For some reason emerald is not avaliable, and I'm more used to arch linux. Discovering that the package is not avaliable in 16.04, My window buttons broke when running compiz --replace. As of now I am using cinnamon until then. I guess I'm a bit used to arch. Please help! Thanks


- Gabe

---

### Post by CantankRus on 2016-11-27
Install ccsm and check the window decorations are enabled.
```
sudo apt install compizconfig-settings-manager
```
Decorations are provided by /usr/bin/gtk-window-decorator


You could also switch to the default xfce window manager, xfwm4.
```
xfwm4 --replace
```

---

