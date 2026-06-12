---
title: "Gnome 3 make super key open application menu instead of overview?"
date: 2013-03-07
forum: General Help
---

### Post by Champlin93 on 2013-03-07
What is the easiest way to make the super key open the application menu in Gnome 3.6? Gnome seems to be the few DEs that do not do this by default.

---

### Post by kclark on 2013-03-07
It should be something like this

```
gconftool-2 --set /apps/metacity/global_keybindings/panel_main_menu --type string "Super_L"
```

Though don't quote me on that it's for 9.10 and Im not in front of my machine to test it on 12.10

---

### Post by markbl on 2013-03-07
> **Champlin93 said:**
> What is the easiest way to make the super key open the application menu in Gnome 3.6? Gnome seems to be the few DEs that do not do this by default.
It already does. Press super and then type the first few letters of the name of the app (or a keyword related to it etc). That's quicker than sifting through menus or icons. Add frequently used apps to your launcher/dash.

---

### Post by Champlin93 on 2013-04-01
I realize all that but I don't have a use for using the super key to opening overview.  It really doesn't make much of a difference but it's more convenient if you can navigate categories rather than just viewing open windows and i'd still have the ability to search witch is what i do most of the time i hit super key anyways.

---

### Post by Champlin93 on 2013-04-01
nope didn't work

---

