---
title: "config file's locations"
date: 2007-11-01
forum: General Help
---

### Post by snickers295 on 2007-11-01
hi i hope this is the right place to put this.
i want to know were all of my config files are so a can know how to configure my system without the GUIs.
i was wanting all of the config file to were i could configure my system as well as using all of the GUIs.

---

### Post by por100pre1 on 2007-11-01
Most of your configuration files are in your user folder. However most system settings (those that require super user) are in other folders. If using Gnome, the .gconf folder is a good place to take a look.

---

### Post by aidanr on 2007-11-01
User config files would be hidden in your home directory (Ctrl+H in nautilus to view them), system wide config files would be in /etc. Of course be careful when manually editing config files, have a back up in case things go wrong.

---

### Post by por100pre1 on 2007-11-01
> **aidanr said:**
> User config files would be hidden in your home directory (Ctrl+H in nautilus to view them), system wide config files would be in /etc. Of course be careful when manually editing config files, have a back up in case things go wrong.

Agree with Aidanr. Always do this before editing a system file:

```
sudo cp */path/of/file* */path/of/file_backup*
```

---

### Post by snickers295 on 2007-11-01
i don't plan on using them, i just want to know in case of a crash or something.

---

