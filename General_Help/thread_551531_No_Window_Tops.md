---
title: "No Window Tops"
date: 2007-09-15
forum: General Help
---

### Post by xelapond on 2007-09-15
I just installed compiz fusion using this guide:

[http://ubuntuforums.org/showthread.php?t=463791]("http://ubuntuforums.org/showthread.php?t=463791")

After running _compiz --replace -c emerald_, and then _emerald --replace _ in Terminal, most of the features work, like expo, and desktop cube.  However the tops(title bar) of my windows are all gone!!

ANy idea on how to get these back?  I kinda need them:)


Any help would be appreciated.

---

### Post by Happy_Man on 2007-09-15
Well, first open CompizConfig Settings Manager, and double-check that the "Window Decorations" plugin is checked. If that's not it, enter ```
emerald --replace
``` in Terminal, and see what errors (if any) it gives. And, just to see if it works, enter ```
gtk-window-decorator --replace
``` If you installed the compiz-gnome package, it should give you your metacity borders.

---

### Post by xelapond on 2007-09-15
Thank you so much.  All it was was the windows decorations checkbox.  was unchecked.

---

