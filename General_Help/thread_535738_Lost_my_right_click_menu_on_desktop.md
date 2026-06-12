---
title: "Lost my right click menu on desktop"
date: 2007-08-26
forum: General Help
---

### Post by cycleger on 2007-08-26
I have lost the right click menu ability on my desktop for both gnome desktop and fluxbox. I'm running a standard and fairly fresh install of Fiesty( 3 or 4 days old). I installed fluxbox from source yesterday  without a hitch, everything has been fine. I noticed today the right-click menu on the gnome desktop was missing. It works with any application as normal the problem is just on the desktop . When I switched over to fluxbox everything worked as expected for several hours then suddenly it wasn't working. Same story just the desktop.  A bit annoying in fluxbox. I wasn't really doing anything at the time, can't explain it!
 So where might I look to find a clue to this menus configuration? I'm drawing a blank! 
 It's a new install and it would not be a great hardship to reinstall but thats too easy!

Any help would be greatly appreciated! 
Thanx in advance
cycleger

---

### Post by jordanmthomas on 2007-08-26
press alt + f2
type
```
gconf-editor /apps/nautilus/preferences
```
and hit enter.

Make sure that on the right, **show_desktop** is checked.
It may require a logout and login to take effect.

If it still doesn't work make sure nautilus is running.

Not sure how to fix your fluxbox problem...are you sure you haven't mapped your right mouse button to do something else?

---

### Post by cycleger on 2007-08-27
show_desktop is checked, and no I haven't  mapped the mouse buttons. I think I'm looking at a progressive problem. Now I startup with a solid background color, I did have a wallpaper up. I use wallpaper-tray which has always worked and does work when clicked but it doesn't put one up at startup. Nautilus is running.

---

### Post by RedSquirrel on 2007-08-27
If you run Nautilus in Fluxbox, you have to run it with the --no-desktop option to prevent it from taking over the desktop:

```
nautilus --no-desktop
```

As for the right-click menu in GNOME, I'm not sure. I don't use GNOME these days...

---

### Post by cycleger on 2007-08-27
Already got it.
This is how I have it set in my fluxbox menu, it's always worked this way;

[submenu] (File utils)
      [exec] (nautilus) {nautilus --no-desktop --browser}
[end]

 I deleted .gnome and .gnome2 and rebooted, I regained my right-click menu and normal wallpaper function in gnome but fluxbox still has no menu. The gnome desktop and nautilus all seem normal and functioning properly but I'm stumped as to why fluxbox  doesn't have menus. Next step may be to try fluxbox-generate_menu.

---

### Post by jordanmthomas on 2007-08-28
I just had the same problem in openbox after editing my menu.

Make ABSOLUTELY sure your menu in fluxbox is syntactically correct.  I accidently put two ending tags on a menu item in openbox, which made it stop working.  (I assume fluxbox would stop working right under the circumstances as well, since openbox and fluxbox are basically the same thing)

I'd just move my current menu elsewhere and rebuild it by copy / pasting parts that look right back into a new menu file.

---

### Post by RedSquirrel on 2007-08-28
> **cycleger said:**
> I'm stumped as to why fluxbox  doesn't have menus. Next step may be to try fluxbox-generate_menu.

Yes, you could generate another menu. The Howto in my signature might help with that.

The file ~/.fluxbox/init has a resource 'menuFile' which points to the file Fluxbox uses for the menu.

If you want to debug your current menu, you could post the output of:

```
grep menuFile ~/.fluxbox/init
```and the *contents* of the file that init is pointing to.

---

