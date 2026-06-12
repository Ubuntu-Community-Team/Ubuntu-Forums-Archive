---
title: "Put display to sleep crashes X"
date: 2006-10-26
forum: General Help
---

### Post by Jonathan Métillon on 2006-10-26
I just updated from Dapper to Edgy. =D>

When the computer goes to screensaving or sleeping display, x server crashes.

I can't even open the screensaver manager to disable it: when I launch the application it crashes the same. Instead I can open Power Management Preferences, so I set* "Put display to sleep when computer is inactive" *to [I]never.

[/I]But it does not solve the problem, I don't want my screen to keep displaying when I'm not using it. Someone encounter a similar issue? Any idea?

---

### Post by autocrosser on 2006-10-27
Are you using wallpaper-tray or desktop drapes? There is a known bug that will cause X to freeze when a desktop switcher tries to change (drove me crazy for a couple of weeks!!!)---I also use Xscreensaver instead of Gnome-screensaver (personal pref) the old Dapper guide still works in Edgy--

---

### Post by Jonathan Métillon on 2006-10-27
Not using wallpaper-tray nor desktop drapes!

But now that I set* "Put display to sleep when computer is inactive" *to *never *the crash did not happen again. It seems that it is related to the new power managment included in GNOME 2.16.

Now the system goes to screensaving with a blank screensaver and does not crash.

---

### Post by Jonathan Métillon on 2007-01-21
I think the issue was not related to the screen saver but by XGL and/or DRI modules that the screen saver uses.

See [this thread]("http://ubuntuforums.org/showthread.php?p=1793987#post1793987") for that issue.

---

