---
title: "disable/remove close button from title bar"
date: 2012-11-08
forum: General Help
---

### Post by spiritech on 2012-11-08
i am trying to remove the close button from the title bar. i have set the metacity general option to minimize,maximize: this worked before, is there a reason why it might not be working now?

spiritech

---

### Post by stinkeye on 2012-11-08
Settings are now in dconf instead of gconf.
Can set in dconf-editor navigating to *org > gnome > desktop > wm > preferences > button-layout*

or use the terminal.
Get current setting...
```
gsettings **get** org.gnome.desktop.wm.preferences button-layout
```

Use custom setting
```
gsettings **set** org.gnome.desktop.wm.preferences button-layout **minimize,maximize:**
```

Reset to default
```
gsettings **reset** org.gnome.desktop.wm.preferences button-layout
```

---

### Post by spiritech on 2012-11-08
> **stinkeye said:**
> Settings are now in dconf instead of gconf.
Can set in dconf-editor navigating to *org > gnome > desktop > wm > preferences > button-layout*

or use the terminal.
Get current setting...
```
gsettings **get** org.gnome.desktop.wm.preferences button-layout
```Use custom setting
```
gsettings **set** org.gnome.desktop.wm.preferences button-layout **minimize,maximize:**
```Reset to default
```
gsettings **reset** org.gnome.desktop.wm.preferences button-layout
```


thankyou, i did have a look through the dconf before, with no avial. 
i take it gconf is depricated now.

---

