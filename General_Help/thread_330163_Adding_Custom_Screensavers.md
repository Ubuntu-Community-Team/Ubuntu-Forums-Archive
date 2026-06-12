---
title: "Adding Custom Screensavers"
date: 2007-01-02
forum: General Help
---

### Post by xGutsAndGloryx on 2007-01-02
How do i add different screensaves in Linux?

---

### Post by jpkotta on 2007-01-02
> **xGutsAndGloryx said:**
> How do i add different screensaves in Linux?

Install all of the xscreensaver data packages: xscreensaver-data xscreensaver-data-extra xscreensaver-gl xscreensaver-gl-extra

---

### Post by xGutsAndGloryx on 2007-01-03
i downloaded a screensavers from Kde-Look website. i am not sure how to get it to work?

---

### Post by jpkotta on 2007-01-03
I don't use KDE, and I don't use KDE's screensaver frontend, which you probably do.  I can tell you this much:

The actual screensaver is nothing more than a program that draws on the screen.  It probably has a .kss extension.  You can find it with the command:
```
locate -r kss$
```
You can run the program like any other.

I think adding it to the list of available screensavers involves a .desktop file.

---

