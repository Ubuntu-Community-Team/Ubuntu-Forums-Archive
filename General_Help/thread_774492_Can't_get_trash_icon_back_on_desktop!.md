---
title: "Can't get trash icon back on desktop!"
date: 2008-04-29
forum: General Help
---

### Post by metrorat on 2008-04-29
Hi all - I'm having a problem with Nautilus (i think) in 8.04.  I have recently been tinkering with Mac4Lin to get an OSX look and now have it pretty much perfect.  However I am unable to get my Trash icon back on desktop where it was before i mucked about with my gnome config files (meaning I deleted them to get rid of a persistent Gnome Settings Daemon error).

Gconf-editor is set correctly with a tick for the desktop trash icon. Tried using gTweakUI to do the same (I know its just a frontend for the gconf but I get a bit superstitious when things don't work) - both to no avail.  Also tried reinstalling nautilus and gnome-applets but nothing i have tried will get that little mother back where he belongs. I am able btw to add the trash icon (which appears in its correct OSX guise) to the Gnome panel and it seems to work fine, so I think it must be some kind of problem with Nautilus drawing the desktop. 

I saw a thread in the Hardy Development Forum (now closed) where someone had a similar problem but I found no solution there. Can anyone help? :confused:

---

### Post by GrouchoMarx on 2008-04-30
Try deleting (or just temporarily moving) the ".nuatilus" folder in your home directory. Then restart nautilus. This should reset all of nautilus' meta-data. Note that if you uninstalled nautilus without "purging" the config data, then it will have remained in your home directory.

---

### Post by metrorat on 2008-04-30
Nice one Groucho - you were exactly right... I had simply selected the reinstall option in Synaptic and all my saved sessions were still there. Renamed the folder, logged out and back in and when I changed the gconf settings it worked! Thanks mate.

---

### Post by Nevermor7 on 2009-08-19
you can also right click and "add to panel" it back...

---

