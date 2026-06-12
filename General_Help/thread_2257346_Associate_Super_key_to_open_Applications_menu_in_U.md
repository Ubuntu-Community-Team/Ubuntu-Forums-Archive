---
title: "Associate Super key to open Applications menu in Ubuntu 14.04 in flashback session"
date: 2014-12-19
forum: General Help
---

### Post by krishna.988 on 2014-12-19
Can someone guide on how to configure Super Key to open Applications menu in ubuntu 14.04 Gnome flashback session? I tried Keyboard option in preferences but couldn't succeed.

---

### Post by ibjsb4 on 2014-12-20
This works in Fallback (metacity).
```
gconftool-2 --set /apps/metacity/global_keybindings/panel_main_menu --type string "Super_L"
```

---

### Post by krishna.988 on 2014-12-20
For Fallback (Compiz) this above code is not working.

---

