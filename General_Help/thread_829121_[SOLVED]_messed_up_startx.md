---
title: "[SOLVED] messed up startx"
date: 2008-06-14
forum: General Help
---

### Post by danbuter on 2008-06-14
I was trying out KDE4, and one of it's options involved replacing a gnome program. Stupidly, I said yes. Now, when I boot my computer, it goes into terminal. (I deleted all the KDE files). While this isn't the end of the world, I'd like to know which gnome program automatically does the startx command so I can fix it. Thanks!

---

### Post by sdennie on 2008-06-14
My guess is that you set the display manager to kdm and, now that it's gone you aren't getting gdm anymore.  Try the following:

```

sudo nano /etc/X11/default-display-manager

```

There should be only one line in that file.  Make sure that line is:

```

/usr/sbin/gdm

```

---

