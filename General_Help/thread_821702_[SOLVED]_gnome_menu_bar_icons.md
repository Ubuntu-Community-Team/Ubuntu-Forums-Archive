---
title: "[SOLVED] gnome menu bar icons"
date: 2008-06-07
forum: General Help
---

### Post by TristanB on 2008-06-07
hi,

I just did a large update with update manager and now the icons next to the text on the menu bar items are gone.  All other icons are fine, they just do not appear on the menu bar/main bar panel applets.

Any ideas?

Thanks,

Tristan

---

### Post by mike2357 on 2008-06-07
This once happened to me, and oddly, rebooting the machine took care of the problem.  The icons reappeared.  If that doesn't work, I'd probably just re-add them one by one.

---

### Post by TristanB on 2008-06-08
Rebooting did not help.  I am not sure what you mean by adding all the icons again.  

I think it has something to do with some gconf setting.  The update seemed to screw up all my settings.  It may have been caused by a crash when I was updating.  I resumed the update after the crash, but maybe some file got deleted and never replaced. 

I ended up with some really odd settings, like with my mouse and keyboard after the update, that I was able to fix, but this icon thing I can't.

The icons are not missing, since they appear correctly on my application launchers on my panel.  They just don't appear along side the name of items in the menu bar, which is frustrating since I find I am much quicker identifying the application I want, if I can see it's icon.

---

### Post by Nepherte on 2008-06-08
What about:
```
update-icon-cache /usr/share/themes/yourthemehere
```
and relogin.

---

### Post by TristanB on 2008-06-09
I tried what you suggested, although it does not fix the problem.

The problem is not with the icon cache.  As I have said the icons appear correctly as launchers on the panel, although do not appear in the menu bar.  The theme choice makes no difference either.  If I go into the main menu editor, then I can see all the icons displayed perfectly.

I still think it has something to do with some gconf settings, as all my setting seemed to have been screwed up after the update.

Thanks,

Tristan

---

### Post by TristanB on 2008-06-19
I deleted my .gconf directory and reinstalled all packages that had anything remotely to do with gnome and finally got my icons back.  It also fixed some other problems I was having.

I think the problem might have been due to the gconf setting becoming corrupted due an aborted update.

---

