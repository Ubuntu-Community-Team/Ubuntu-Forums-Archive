---
title: "Gnome terminal profile"
date: 2007-12-08
forum: General Help
---

### Post by Mramius on 2007-12-08
I use the gnome terminal for a few different tasks and I'm using ccsm to decorate each one accordingly.

However, I'm having trouble launching each gnome terminal with the profile I want it to have.

I'm using:

```
gnome-terminal --title=GIRCC --hide-menubar --profile=PROFILENAME
```

but it isn't loading the profile.  It is giving it the title and hiding the menu bar but it isn't loading the profile.  What am I doing wrong?

---

### Post by p_quarles on 2007-12-08
Try replacing the last option with:
```
--window-with-profile=PROFILENAME
```

---

