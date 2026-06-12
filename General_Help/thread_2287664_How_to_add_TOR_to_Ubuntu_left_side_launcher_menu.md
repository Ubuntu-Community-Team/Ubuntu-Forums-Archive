---
title: "How to add TOR to Ubuntu left side launcher menu?"
date: 2015-07-21
forum: General Help
---

### Post by tdk2 on 2015-07-21
When I launch tor through gnome terminal the Firefox icon on left side launcher menu becomes active as if I have launched Firefox, so I can't lock TOR to the launcher.  Is there a directory I should copy the tor.desktop file to?

---

### Post by Julind on 2015-07-24
Drag and drop the **tor.desktop** file to the launcher, found in [B]/usr/share/applications
[/B]
If there's no tor.desktop file open a terminal and run
```
gnome-desktop-item-edit ~/Desktop/ --create-new
```
from there set the launcher up. It will pop on the desktop which you can run and lock it in the launcher.

If gnome-panel is not found simply install it using 
```

sudo apt-get update
sudo apt-get install gnome-panel
```

---

