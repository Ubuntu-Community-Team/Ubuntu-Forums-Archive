---
title: "Unable to run Steam on 18.04"
date: 2018-04-28
forum: General Help
---

### Post by Sith Lord Kyle on 2018-04-28
Steam seems to update OK but it doesn't run.  When I try to start it via Terminal, I get the following error:

```
Gtk-Message: 21:57:29.118: Failed to load module "gail"
Gtk-Message: 21:57:29.118: Failed to load module "atk-bridge"
dbus[9146]: arguments to dbus_message_new_method_call() were incorrect, assertion "path != NULL" failed in file ../../../dbus/dbus-message.c line 1362.
This is normally a bug in some application using the D-Bus library.
```

Anyone else run into this issue?

---

### Post by tarzip on 2018-04-29
delete ~/.local/share/Steam then try to start steam

You'll have to reinstall games but it will fix it

---

### Post by Sith Lord Kyle on 2018-04-29
Well, now it just gives me a totally different error... but that was easier to fix.  Thanks, sir!

---

