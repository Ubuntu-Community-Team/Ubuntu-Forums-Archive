---
title: "Screen power save isn't working"
date: 2013-10-26
forum: General Help
---

### Post by miceagol on 2013-10-26
In the "Brightness & Lock" settings, the screen is set to turn off when inactive for 5 minutes. However, this isn't happening. What must I do to fix this permanently? I've tried the command
```
xset dpms 300 600
```
but it only worked to begin with, and not anymore.

Suggestions?

---

### Post by ernstp on 2013-10-27
Same problem...

---

### Post by miceagol on 2013-10-27
bump

---

### Post by miceagol on 2013-11-08
I solved this by replacing Gnome 3.8 with Gnome 3.10. I don't know the details of what caused this and why updating Gnome fixed the issue.

Note that upgrading Gnome to 3.10 will break Unity, and you'll have to use the gdm window manager and not lightdm to avoid ending up with no gui.

---

