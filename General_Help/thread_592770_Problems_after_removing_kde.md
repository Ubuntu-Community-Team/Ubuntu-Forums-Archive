---
title: "Problems after removing kde"
date: 2007-10-26
forum: General Help
---

### Post by Prometheus7 on 2007-10-26
I removed KDE and I think that doing this removed some features from Gnome. Specifically, nautilus no longer displays "Extract Here" when I right click on a zipped or tarred file. I tried reinstalling nautilus and tar but neither helped. Does anyone know what the correct package to install is?

Thanks!

---

### Post by taurus on 2007-10-26
Just to be on a safe side, try

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```
It will reinstall those "missing" packages for your Gnome again.

---

