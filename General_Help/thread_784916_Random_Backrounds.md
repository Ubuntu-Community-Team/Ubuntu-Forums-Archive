---
title: "Random Backrounds"
date: 2008-05-06
forum: General Help
---

### Post by raffman on 2008-05-06
I have a bunch of really nice wallpapers and instead of choosing one,I would like a random one to load each time. How do I?

 As a bonus it would be nice if each desktop could have a different wallpaper (also at random)

                                             Thanks!

---

### Post by Monicker on 2008-05-06
The drapes package might work for you, though I don't see any per desktop options.  Its in Synaptic.

---

### Post by aroch1 on 2008-05-16
Wallpapoz is a program that can change your backgrounds randomly, it's not in the repos though (at least I don't believe so) so you'll have to google it.

As far as one wallpaper per desktop, it's a tricky thing to do in gnome.  If you're willing to give up the right-click context menu and icons on your desktop you can disable Nautilus from drawing the desktop by:

Alt+F2 "gconf-editor"

Uncheck apps->nautilus->preferences->show_desktop

Now to get different wallpapers you'll have to have compiz up and running.  Fire up ccsm and go to your cube plugin, where you can specify one wallpaper per side of the cube.  The problem is that if Nautilus is drawing the desktop, it's wallpapers appears over this one.

I don't know if wallpapoz will work with this compiz thing.

You can also supposedly patch nautilus to allow this without disabling anything, but I've tried it twice and not had any luck.

---

### Post by tattrat on 2008-05-17
If you install screenlets, there is a wallpaper changer screenlet available. It works, but it doesn't fade to the next wallpaper, like in Mac os X but it works. 

Like many things, it is in its early days, of development and I am sure it will get better.

---

