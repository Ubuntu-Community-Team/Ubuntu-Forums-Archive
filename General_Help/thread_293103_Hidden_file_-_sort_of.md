---
title: "Hidden file - sort of"
date: 2006-11-04
forum: General Help
---

### Post by MonsterDog on 2006-11-04
Hi,

This isn't an important issue, just a curiosity.  While poking around I found that there is a file that I can find and stat but it doesn't show up in Nautilus.  It's not a dot file, I show those anyway.  The file in question is:  /usr/share/app-install/desktop/libxine-extracodecs.desktop.  Like I said, I'm just curious if anyone knows what's going on.  Are there files that are only hidden to Nautilus?

Thanks,
MD

---

### Post by CatKiller on 2006-11-04
I think you'll find that it's there, but under a different name. 

.desktop files (used for launchers, menu entries and the like) get displayed in Nautilus by their internal name - for localisation reasons.

More info [here]("http://www.freedesktop.org/wiki/Standards/desktop-entry-spec"), if you're interested.

---

### Post by MonsterDog on 2006-11-06
Thanks CatKiller,

Are you sure they didn't to it just to confuse me?  I guess I can live with a little confusion so there can be less confusion.

MD

---

### Post by CatKiller on 2006-11-06
> **MonsterDog said:**
> Are you sure they didn't to it just to confuse me?

:lol: .desktop files are funny things. I'd quite like a way to see their filename in Nautilus. A bug report has been filed, but it's rather old.

If you're interested in knowing which .desktop file is called what, you can use, for example, ```
less /usr/share/app-install/desktop/libxine-extracodecs.desktop
``` and look for the **Name=** line. This will tell you that /usr/share/app-install/desktop/libxine-extracodecs.desktop gets displayed as "Xine extra plugins" - in the Add/Remove programs application, I guess.

---

