---
title: "Screensaver preferences file stored where?"
date: 2007-07-14
forum: General Help
---

### Post by biogon on 2007-07-14
I am on 7.04 Feisty Fawn on a Dell Latitude D630, and I switched to one of the screensavers that causes everything to flicker and crash.

The default screensaver works fine; it's just one of the Ant* ones that does it.

The problem is that anytime the screensaver kicks in, I crash. 

Not only does it crash when it kicks in, it also crashes when I try to open the gnome-screensaver-preferences application from the System menu so I can't switch to a different one. 

Where is the screensaver .conf or pref file so I can delete and/or edit it in a shell?

Thanks!

-j

---

### Post by gfixler on 2007-07-15
Mine is in my home directory, under:

.gconf/apps/gnome-screensaver/%gconf.xml

You can also edit it in the gconf editor, which for me is in the Applications->System Tools menu, as Configuration Editor. From the command line:

gconf-editor

In there, it should be under /apps/gnome-screensaver

---

### Post by biogon on 2007-07-15
gfixler,

Beautiful! Your advice worked perfectly.

Thank you!

-jon

---

