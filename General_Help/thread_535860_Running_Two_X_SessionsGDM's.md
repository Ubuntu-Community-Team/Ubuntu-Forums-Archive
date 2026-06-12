---
title: "Running Two X Sessions/GDM's"
date: 2007-08-27
forum: General Help
---

### Post by norris7 on 2007-08-27
Hi. 
I'd like to run two X sessions and GDM's, one on Alt-F7, the other on Alt-F8. I'm aware that I can do startx -- :2 or whatever from terminal, but this doesn't allow me choose Window Managers like with GDM. What I want is a complete login screen on both sessions available upon bootup. Any tips?

---

### Post by anubhavrocks on 2007-08-27
To star t gdm on say vt10
```
/usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt10
```
Another on vt11
```
/usr/X11R6/bin/X :1 -br -audit 0 -auth /var/lib/gdm/:1.Xauth -nolisten tcp vt11
```

It would be simpler to edit the [servers] section in gdm.conf or use
```
gdmflexiserver
```

---

