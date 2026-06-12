---
title: "firefox crashes"
date: 2007-01-18
forum: General Help
---

### Post by huviduc on 2007-01-18
my firefox crashes immediately when opened, if i uninstall 2.0 and go back to 1.5, it works fine unless i got to a page that uses flash (firefox homepage). i cant seem to get it to work correctly, i readl through some of the other threads and i tried the x.org thing, and my color depth is at 24. how to i know if i have flash installed correctly? or how can i fix this and use firefox again?

i have dapper with both KDE and GDM installed with gdm as default it any of that matters

---

### Post by tronica on 2007-01-18
see what version of flash you have

You might try uninstalling and reinstalling flash

---

### Post by huviduc on 2007-01-18
how can i find out what flash player i have installed if any? i have been trying to reinstall flash 9, but when it asks for a directory to install it to, everytime, it says" WARNING: please enter a valid installation path"

i cant figure out where to put it, or why it wont let me install it anywhere

---

### Post by tronica on 2007-01-18
to install flash open a termial

type
> sudo apt-get install flashplugin-nonfree

then restart firefox

to see what plugins you have install for fox, type this in at the address bar

```
about:plugins
```

---

