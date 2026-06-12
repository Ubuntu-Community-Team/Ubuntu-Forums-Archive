---
title: "Device Manager"
date: 2007-08-20
forum: General Help
---

### Post by NBCChimes on 2007-08-20
I can't seem to get to the Device Manager. I go to System => Administration and I don't see the DM in the list. The items in the list are in alpha order but it starts with Keyring Manager.  What am I missing?

Thanks,
Bill

---

### Post by eggdeng on 2007-08-21
Coud be the menu items are absent because your user hasn't got the right privileges. Try to start it from a terminal with the command ```
hal-device-manager
```

---

### Post by NBCChimes on 2007-08-21
That did it, thanks!

---

