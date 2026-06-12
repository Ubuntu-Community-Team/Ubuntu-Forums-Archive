---
title: "change login window theme?"
date: 2007-07-30
forum: General Help
---

### Post by geminias on 2007-07-30
I need a command line interface to change the login theme.  I changed it via gdmsetup (the Login Manager) and now I can't login to my computer.  After typing name and password it just hangs.  Must be something wrong with the theme I installed...  So i gotta change it back via command line!

---

### Post by Lord Illidan on 2007-07-30
What theme did you install..I'd like a look at it myself.

How to change it back?

From the command line, type sudo nano /etc/X11/gdm/gdm.conf and find this paragraph.

```
# These two keys are for the themed greeter (gdmgreeter).  Circles is the
# standard shipped theme.  If you want GDM to select a random theme from a
# list then provide a list that is delimited by /: to the GraphicalThemes
# key and set GraphicalThemeRand to true.  Otherwise use GraphicalTheme
# and specify just one theme.
GraphicalTheme=Human
```

Make sure that GraphicalTheme=Human.

 You might have to scroll down a few lines, >400 in my case :S

---

### Post by Lord Illidan on 2007-08-03
Hi, did this work for you?

---

