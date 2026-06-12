---
title: "Nautilus on 15.10: Permanently show path"
date: 2016-02-24
forum: General Help
---

### Post by Macamba on 2016-02-24
**How does one get Nautilus to display the path instead of buttons permanently?**

In Nautilus you can switch between the default behaviour and showing the path in the address bar by pressing Ctrl-L. But if you close Nautilus and open it again it has reverted back to its old behaviour. 

I tried to change the behaviour in gconf-editor, but I can not find Nautilus as described in [RestoreNautilusLocationBar]("https://help.ubuntu.com/community/RestoreNautilusLocationBar").

---

### Post by mc4man on 2016-02-24
Use dconf-editor > org > gnome > nautilus > preferences
or from cli 
```
gsettings set org.gnome.nautilus.preferences always-use-location-entry true
```

---

### Post by Macamba on 2016-02-25
Thanks

---

