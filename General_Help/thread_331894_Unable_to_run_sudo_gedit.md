---
title: "Unable to run sudo gedit"
date: 2007-01-05
forum: General Help
---

### Post by JPMaximilian on 2007-01-05
When I'm trying to edit xorg.conf, i try to run 

```
sudo gedit /etc/X11/xorg.conf
```

But the terminal window will just hang, so i end up CTRL-C and having to run pico or something like that.  Whats the deal?

---

### Post by taurus on 2007-01-05
```
gksudo gedit /etc/X11/xorg.conf
-or-
sudo nano -w /etc/X11/xorg.conf
```

---

### Post by JPMaximilian on 2007-01-05
Thanks for the alternatives, but why is it that sudo gedit works sometimes but not others?

---

### Post by taurus on 2007-01-05
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by meng on 2007-01-05
sudo isn't recommended for running graphical apps.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
Doesn't answer your question fully though.

---

