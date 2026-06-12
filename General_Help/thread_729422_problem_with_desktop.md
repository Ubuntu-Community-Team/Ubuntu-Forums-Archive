---
title: "problem with desktop"
date: 2008-03-19
forum: General Help
---

### Post by gsb521 on 2008-03-19
Every time I boot my laptop, I get a fully functional Ubuntu interface including the toolbars, but the desktop background doesn't work right - it is solid black rather than my wallpaper image, the icons that are in the desktop folder aren't there, and it is not right-click-able.  I can change the wallpaper through system-preferences-appearance, but it just resets to black when I boot again.

Before this recent problem, it had been fine for months without many changes.

---

### Post by phiphedog on 2008-03-19
You could try to reinstal GNOME with

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

