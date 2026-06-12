---
title: "fails to boot correctly, then error message"
date: 2006-12-15
forum: General Help
---

### Post by GazzaK on 2006-12-15
I have a problem where Ubuntu 6.10 with beryl 1.3 takes ages to display the desktop after a successful login.

It sits there, with a light grey box taking up 1/4 of the screen (top left side) and only the cursor, then after a few minutes the login splash appears, the login sound plays and the desktop is displayed, but looking different, and this error message is displayed

[IMG]http://ubuntuforums.org/gallery/data/549/error.jpg[/IMG]

My icons etc are all different, but if I Close that error and goto System>Preferences>Themes they appear (without me selecting anything)

all else seems okay, and I can switch between beryl and metacity no problem.

Any idea?

Gary

---

### Post by xopher on 2006-12-15
Try running gnome-settings-daemon from terminal:

```
gnome-settings-daemon
```

Are you running Beryl with the gnome-session? (So it auto-loads.) If so, try disabling that, leaving gnome to load normally - and run Beryl when you have successfully logged in.

---

### Post by GazzaK on 2006-12-15
If I disable beryl, it still takes just as long to do anything, but when it does finally start it is using metacity.

and running gnome-settings-daemon from terminal while X is stuck fails 
> Gtk-WARNING **:cannot open display

So sadly neither of those options helped at all :-(

---

### Post by GazzaK on 2006-12-15
this was fixed by uninstalling beryl completely and reinstalling...

---

