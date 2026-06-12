---
title: "runlevel"
date: 2005-08-12
forum: General Help
---

### Post by lee_connell on 2005-08-12
hey all i went to switch the runlevel from 2 to something else and it still brings up X.

What do i do to stop X from running when booting the computer.  I don't want to use single user mode.  I looked in /etc/rc*.d and i didn't see anything for X in there?

---

### Post by varunus on 2005-08-12
GDM is the thing that stops X.  If you want to stop X from starting but be in multi-user mode, just type the following in a terminal:

```
sudo update-rc.d -f gdm remove
```

GDM is the script that starts X.

If you do this, you can still start X by typing startx, of course.

---

