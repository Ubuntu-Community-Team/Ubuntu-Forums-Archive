---
title: "Creating a Logoff shortcut???"
date: 2007-11-24
forum: General Help
---

### Post by Guardian-Mage on 2007-11-24
People, come on now, seriously, in Windows I click new shortcut, logout and it's done. But no, in Ubuntu it's not that simple. I love Ubuntu, could somebody tell me how to bring up the logout dialog in GNOME and XFCE, and if you know how, how would I bring up the same dialog as I would get from the GNOME Quit Applet? Thanks, forgive me for whining

---

### Post by Guardian-Mage on 2007-11-24
I figured it out, for anyone who wants to know how, create a launcher with the type set to Application and the command set to gnome-session-save --kill

---

### Post by mali2297 on 2007-11-24
In XFCE, it's
```

xfce4-session-logout

```

---

### Post by axel_oxenstierna on 2007-11-26
gnome-session-save --kill

Worked like a charm as a launcher from AWN starter bar!

Thx!

---

