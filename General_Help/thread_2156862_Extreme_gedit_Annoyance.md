---
title: "Extreme gedit Annoyance"
date: 2013-06-23
forum: General Help
---

### Post by r_avital on 2013-06-23
Using Raring Ringtail 64bit freshly installed.

Double-clicking on anyfile.txt in dolphin, opens up the file in gedit as expected.

But it also opens an empty document.  Every.Single.Time.  So closing your document always brings up the "save untilted document 1 before closing" dialog.  Extremely annoying.

What I've tried, unsuccessfully:
1. /usr/share/applications/gedit.desktop - every entry reading "Exec-gedit etc" changed to "gedit $1 < /dev/null" - no effect.
2. Within dolphin, used "open with" and specified "gedit $1 < /dev/null" - no effect.
3. Within dolphin, used "open with" and specified "gedit %U" - no effect.
4. Within dolphin, used "open with" and specified "gedit" - no effect.

Anyone, any ideas, please?

Thanks in advance.

---

### Post by vasa1 on 2013-06-23
Are you logged in as root when this happens? If so, it maybe a known bug.

Also, see if any of these relate to you:
[https://bbs.archlinux.org/viewtopic.php?id=120283](https://bbs.archlinux.org/viewtopic.php?id=120283)
[https://bugs.kde.org/show_bug.cgi?id=276103](https://bugs.kde.org/show_bug.cgi?id=276103)
[https://bugs.mageia.org/show_bug.cgi?id=2519](https://bugs.mageia.org/show_bug.cgi?id=2519)

---

### Post by HiImTye on 2013-06-23
use [vim]("apt://vim-gnome") ;)
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by kurt18947 on 2013-06-24
That irritant seems to be fixed in 13.10 - so far at least.  You could download leafpad as a replacement or alternative to gedit.

---

### Post by r_avital on 2013-06-24
vasa1,

Thanks for the suggestions, I had actually found them and tried them out before I posted here (none solved the problem for me), but since we now know it's a "feature" and it's been fixed in an upcoming release, I can live with it for a little while.

Thanks everybody for your responses!

Cheers

---

