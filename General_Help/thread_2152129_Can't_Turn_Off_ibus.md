---
title: "Can't Turn Off ibus"
date: 2013-06-06
forum: General Help
---

### Post by Tk007LwZFJW5ej on 2013-06-06
I cannot figure out how to stop ibus from starting up with the system. It's not in the list of applications that are set to run when I log in.

---

### Post by greatsirkain on 2013-06-07
well ibus uses dbus & dbus is a startup application but I really don't know what would happen if you disabled it
dbus is hidden by defaul along with a few other things
```
sudo sed -i "s/NoDisplay=true/NoDisplay=false/g" /etc/xdg/autostart/*.desktop
```
to show hidden items in the startup manager

---

