---
title: "Error activating XKB configuration."
date: 2013-03-02
forum: General Help
---

### Post by arthropode on 2013-03-02
Hello,

I had a bug : each time I connected a keyboard, a mouse to my computer or I woke my computer up this error message printed : 
```
Erreur à l'activation de la configuration XKB.
Il peut y avoir plusieurs raisons à cela.

Si vous ouvrez un rapport d'anomalie, merci d'y inclure les résultats de
 &#8226; xprop -root | grep XKB
 &#8226; gsettings get org.gnome.libgnomekbd.keyboard model
 &#8226; gsettings get org.gnome.libgnomekbd.keyboard layouts
 &#8226; gsettings get org.gnome.libgnomekbd.keyboard options
```

In english : 
```
Error activating XKB configuration. 
It can happen under various circumstances. 


If you report this situation as a bug, please include the result of: 
 &#8226; xprop -root | grep XKB
 &#8226; gsettings get org.gnome.libgnomekbd.keyboard model
 &#8226; gsettings get org.gnome.libgnomekbd.keyboard layouts
 &#8226; gsettings get org.gnome.libgnomekbd.keyboard options


```
Here are the results of : 
xprop -root | grep XKB : ```
_XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "pc105", "fr", "mac", ""
_XKB_RULES_NAMES(STRING) = "evdev", "applealu_iso", "fr", "", "grp:shift_caps_toggle"
```

gsettings get org.gnome.libgnomekbd.keyboard model : ```
'applealu_iso'
```

gsettings get org.gnome.libgnomekbd.keyboard layouts : ```
['fr']
```

gsettings get org.gnome.libgnomekbd.keyboard options : ```
['grp\tgrp:shift_caps_toggle']
```


It was only with gnome, with only Openbox it was for example OK.

However, I fund that it made it only if my keyboard was configure in some configurations, french (variant) or french (bépo) for example. In other configurations, I don't have this problem, for example in french, or french (swiss).
So, I know now how to avoid thisbug, but I would know what really happend

(I have Ubuntu 12.04 LTS)

---

### Post by arthropode on 2013-03-03
No one have an idea ?

---

