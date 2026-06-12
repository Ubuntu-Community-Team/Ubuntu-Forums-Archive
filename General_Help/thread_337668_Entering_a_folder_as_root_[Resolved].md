---
title: "Entering a folder as root [Resolved]"
date: 2007-01-13
forum: General Help
---

### Post by bg1256 on 2007-01-13
I'm trying to install a cairo-clock theme from gnome-look.org, and according to the instructions:

```
then you must go to /usr/share/cairo-clock/themes with root permission of course then...you just simply drag and drop the folder taht contains the clock theme, then you restart the clock and thats it..cheers
```

How do I enter this folder as root?

---

### Post by NeoLithium on 2007-01-13
If you're using gnome, type:  alt+f2 and type in:
```

gksudo nautilus /usr/share/cairo-clock/themes

```

---

### Post by bg1256 on 2007-01-13
Thanks much!

---

### Post by yopnono on 2007-01-13
> **NeoLithium said:**
> If you're using gnome, type:  alt+f2 and type in:
```

gksudo nautilus /usr/share/cairo-clock/themes

```

Or if on Edgy install nautilus-gksu = context menu to open any file/folder as root.
Or use a nautilus script or create a nautilus action that does the same.

---

