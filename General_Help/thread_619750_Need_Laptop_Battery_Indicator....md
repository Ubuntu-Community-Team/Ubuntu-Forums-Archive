---
title: "Need Laptop Battery Indicator..."
date: 2007-11-21
forum: General Help
---

### Post by jskidmore on 2007-11-21
Hi, I just installed Xubuntu and have been doing a little configuration, but I just noticed that there is no battery indicator on the desktop anywhere (I'm on a laptop).

How can I get a status indicator (showing the percent left, etc.)?

Thanks!

---

### Post by prince_niceguy on 2007-11-21
go to preferences --> power management. It should give list of options. select always display icon.

---

### Post by jskidmore on 2007-11-21
I ended up installing gnome-power-manager:
```
sudo apt-get install gnome-power-manager
```

Nothing happened after I installed it, but when I ran the preferences command, it all showed up:
```
gnome-power-preferences
```

---

### Post by akshunj on 2007-11-22
XFCE also has a tray icon with battery stuff in it...

---

### Post by santiagoward2000 on 2007-11-22
> **akshunj said:**
> XFCE also has a tray icon with battery stuff in it...

That's right! Just right-click on a panel, go to **Add New Item** and look for it there.

---

