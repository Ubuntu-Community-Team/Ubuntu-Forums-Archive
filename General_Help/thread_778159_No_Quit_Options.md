---
title: "No Quit Options"
date: 2008-05-01
forum: General Help
---

### Post by pdoma on 2008-05-01
After installing xubuntu 8.04 I realized when you click on quit the menu with (shutdown, reboot, logout, hibernate, etc.) does not show up, instead the current session just ends and you get kicked out to the main login window. From there you can pick shutdown or reboot which works fine but does any one know how to get the menu working when you click on quit?

Thanks.

---

### Post by zvacet on 2008-05-02
Try to right click on it and remove it from panel and add it again.If that doesn´ work try 

```
killall gnome-panel
```

and if still no luck maybe update will fix it.Until then you can shutdown with this

```
sudo shutdown -h now
```

---

