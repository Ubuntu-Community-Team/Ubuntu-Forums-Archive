---
title: "*** glibc detected *** double free or corruption"
date: 2006-07-28
forum: General Help
---

### Post by rmjb on 2006-07-28
Hi, my samba share was working but now, for some reason it's not. I get the error

```
*** glibc detected *** double free or corruption
```

whenever I launch shares-admin from the terminal. If I launch it from the menu the window appears, with nothing enabled, then disappears.

Anyone knows what could be the problem?

- rmjb

---

### Post by kswnsn on 2006-10-10
If you are/have run KDE, and selected a certain GTK style under the KDE control center, you will have a ~/.gtkrc-2.0 file that will prevent certain GNOME apps from running.  First rename this file to see if it clears the issue, and if so, try a different theme.  I was using "Glider" but changed to  "Human" to correct this issue.

See also:  [http://ubuntuforums.org/showthread.php?t=261494&highlight=glibc+detected](http://ubuntuforums.org/showthread.php?t=261494&highlight=glibc+detected)

---

### Post by rmjb on 2006-10-10
Wow this is an old thread that you answered. Thanks for the response though. I'm not running KDE unfortunately. I think at the time I was having this problem there was an issue with a recent samba update. It's since been updated again and everything seems to be fine since then.

- rmjb

---

