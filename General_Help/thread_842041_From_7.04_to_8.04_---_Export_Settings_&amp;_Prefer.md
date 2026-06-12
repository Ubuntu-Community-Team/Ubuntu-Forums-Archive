---
title: "From 7.04 to 8.04 --- Export Settings &amp; Preferences ?"
date: 2008-06-27
forum: General Help
---

### Post by nooblot on 2008-06-27
I'm doing a complete new install of 8.04 --- is there some tool or methods  in 7.04 to export settings and preferences (at least for Gnome) ?
...or I have do this all over again

thanks

---

### Post by p_quarles on 2008-06-27
All of your settings are stored in your home folder. You can keep those by either saving a copy of your entire home folder, or by keeping copies of directories containing settings for the programs that you specifically want. 

Many Gnome programs have their own hidden directories, such as
```
/home/username/.pidgin
```
Global Gnome settings are in
```
/home/username/.gconf
```
And so forth.

---

