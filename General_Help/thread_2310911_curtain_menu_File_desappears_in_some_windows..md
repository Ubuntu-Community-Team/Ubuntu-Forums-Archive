---
title: "curtain menu File desappears in some windows."
date: 2016-01-22
forum: General Help
---

### Post by luca-dgh on 2016-01-22
I recently upgraded from 12.04 to 14.04 Gnome Flashback, I have 2 users.
In User 1 some windows like SimpleScan or Mahjiongg doesn't have the menu bar where there are some buttons like "File" (or other names for that button). The strange is that in User 2 the same windows have that bar.
I attach 2 screenshots to explain better the problem.
How can I have that bar in User 1?
I tried to surf dconf , but I found nothing.
Thx a lot for your help.

---

### Post by luca-dgh on 2016-02-02
Bump!
Please, nobody as an idea?

---

### Post by luca-dgh on 2016-02-03
Found the solution in an old thread in a Fedora users forum:
[http://forums.fedoraforum.org/showthread.php?t=293685](http://forums.fedoraforum.org/showthread.php?t=293685)
the trick was this:
```
gsettings set org.gnome.settings-daemon.plugins.xsettings overrides '{"Gtk/ShellShowsAppMenu":<0>}'
```

---

