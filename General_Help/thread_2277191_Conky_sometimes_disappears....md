---
title: "Conky sometimes disappears..."
date: 2015-05-07
forum: General Help
---

### Post by timgood on 2015-05-07
I wonder if anyone has the solution to this annoyance: I have looked on the InterWeb, but so far, nothing doing. I have a conky which runs flawlessly in 14.10, but which sometimes disappears for a few moments or longer in 15.04 when an application is launched or closed, or when a notification icon or the desktop is clicked. I have tried various settings to no avail. My current conky window settings are:

```
# Window specifications #

own_window_class Conky
own_window yes
own_window_type conky
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_argb_visual yes
```

Other own_window_type settings like override, dock, desktop result in black background or conky showing over windows. Any ideas?

---

### Post by Frogs Hair on 2015-05-07
What window types have you tried ?```
 own_window_type conky
``` Alternatives might include desktop, override, or panel. In regular Ubuntu the file manager handles the desktop so I find necessary to change the window type for some conky scripts so it doesn't go missing when the desktop right clicked .

---

### Post by timgood on 2015-05-07
I have tried desktop, override, panel and dock. Override keeps it above windows, as does dock (but override also turns background black). Desktop also disappears. I have also tried normal. No dice! I suspect this may be something to do with compositing in Plasma 5.

---

### Post by Frogs Hair on 2015-05-07
Do you use Kwin or compiz ?

---

### Post by timgood on 2015-05-08
> **Frogs Hair said:**
> Do you use Kwin or compiz ?

Using standard Kwin. Some compiz packages not available for Kubuntu 15.04

Installed available compiz packages, but when window manager is switched, conky has black background.

---

### Post by timgood on 2015-05-09
Changed window type to override today, and it's now working with full transparency and no disappearances! Previously has turned panel black. Don't know why it's working now, but  will mark this solved.

---

### Post by Frogs Hair on 2015-05-09
Weird ! glad it worked out.

---

