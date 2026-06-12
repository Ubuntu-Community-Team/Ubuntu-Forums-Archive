---
title: "wallpaper-tray isn't working without nautilus"
date: 2008-07-02
forum: General Help
---

### Post by ifreecarve on 2008-07-02
i'm using wmii, and i am trying to set up wallpaper-tray to manage my desktop background.  because wmii doesn't have the gnome system tray, i'm using trayer (tried stalonetray too).  

the problem i'm seeing is that, although wallpaper-tray properly scans my images directory and creates a thumbnail for the tray icon, it does not actually SET the background in wmii.

wallpaper-tray works fine in gnome.  also, if i load up nautilus in wmii, wallpaper-tray will properly set and cycle the images -- but when i close nautilus, that functionality stops (it keeps the existing wallpaper but doesn't change it to new ones).  one last thing, when i pick a wallpaper while in wmii (whose thumbnail i see in the trayer icon), that wallpaper will be the one i see if i switch to gnome.  

to me, this suggests that running nautilus sets up some process that actually performs the wallpaper configuration when wallpaper-tray requests it.  the only problem is that i can't figure out how to set that up in a non-gnome window manager.

has anyone been able to set up wallpaper-tray without the nautilus desktop?

---

### Post by ifreecarve on 2008-07-04
After some digging, it looks like this may be the culprit:
[http://bugzilla.gnome.org/show_bug.cgi?id=531487](http://bugzilla.gnome.org/show_bug.cgi?id=531487)

Where can I find out whether this change has been picked up by Ubuntu?  

In the meantime, does anyone know of a program (or snippet of code) to force gnome-settings-daemon to apply_prefs?

---

### Post by ifreecarve on 2008-07-10
```
xsetbg -border black "`gconftool-2 --get /desktop/gnome/background/picture_filename`"
```

this is the workaround that i'm using for now.  

thanks for the enthusiastic response, it was really helpful.

---

