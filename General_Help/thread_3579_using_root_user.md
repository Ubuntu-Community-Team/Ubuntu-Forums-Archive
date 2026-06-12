---
title: "using root user"
date: 2004-11-07
forum: General Help
---

### Post by Pulka on 2004-11-07
Since i'm using ubuntu i'm having many problems with permissions. With other distros, i used a simple solution: login as root; but now, i can't do that. When i have a folder thar doesn't have permissions, i don't know how to change it. I know i can do it in terminal using sudo, but i prefer using the graphical way. How can i do it?

---

### Post by diebels on 2004-11-07
You can use gksudo. gksudo $PROGRAMNAME
Like "gksudo gedit" or "gksudo nautilus".
Use [ALT]+[F2] to get the run dialog.

---

### Post by Pulka on 2004-11-07
done. Thanks!

---

### Post by tvlad on 2004-11-07
You could also do sudo [Program] from a console within gnome, or sudo su root in a normal terminal then run programs as a root .

---

### Post by p!=f on 2004-11-07
```

sudo -s

```

---

