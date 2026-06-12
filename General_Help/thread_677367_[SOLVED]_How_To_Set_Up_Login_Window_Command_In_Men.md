---
title: "[SOLVED] How To: Set Up Login Window Command In Menu"
date: 2008-01-24
forum: General Help
---

### Post by Mark76 on 2008-01-24
I didn't like the default xfce4 menu editor so I made my own menus and now I can't access the login window gui.

I'm using GDM and it'd be nice if I could actually get into the login window gui to add a new theme.

---

### Post by PeterJS on 2008-01-24
The gdm developers were really creative with their naming :) the name of the program to set up gdm is gdmsetup. It's going to want to be run with root privilages, so for a menu entry I'd suggest a command of:
```

gksudo gdmsetup

```

---

### Post by Mark76 on 2008-01-24
That's the one :)

Can I use the same command (appropriately edited) for other DMs?

---

### Post by PeterJS on 2008-01-24
The same command should work from any DE to configure GDM. I don't think KDM has an equivalent command, I think the only way to get at it is through KControl.

---

### Post by Mark76 on 2008-01-24
Thanks :)

---

