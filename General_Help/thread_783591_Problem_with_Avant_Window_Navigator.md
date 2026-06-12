---
title: "Problem with Avant Window Navigator"
date: 2008-05-05
forum: General Help
---

### Post by gkrules on 2008-05-05
whenever i start AWN all of the icons move up and i cant click on the bar at the bottom

how do i fix this?

here's a screenshot of what's happening:
they're supposed to rest on the bar...

[[IMG]http://img257.imageshack.us/img257/2325/screenshotgj4.th.png[/IMG]](http://img257.imageshack.us/my.php?image=screenshotgj4.png)


im running hardy heron

---

### Post by c4v3m4n on 2008-05-05
I can't see your screenshot, but have you tried restarting awn? Does it continue to occur if you log out and log back in?  My awn bar has tweaked out a few times but restarting it or logging out and back in has always worked for me.

---

### Post by danpos on 2008-05-05
@All

You must to reset yours awn settings:

1. Uninstall awn and related programs;
2. Remove ~/.config/awn and ~/.gconf/apps/avant-window-navigator;
3. At terminal:
```
gconftool-2 --recursive-unset /apps/avant-window-navigator
```

After that, reinstall awn and everything will work OK.

That's all.

Regards,

Danpos.

---

### Post by gkrules on 2008-05-06
> **danpos said:**
> @All

You must to reset yours awn settings:

1. Uninstall awn and related programs;
2. Remove ~/.config/awn and ~/.gconf/apps/avant-window-navigator;
3. At terminal:
```
gconftool-2 --recursive-unset /apps/avant-window-navigator
```

After that, reinstall awn and everything will work OK.

That's all.

Regards,

Danpos.


thanks it worked

---

### Post by danpos on 2008-05-09
> **gkrules said:**
> thanks it worked

Your welcome. :)

Danpos.

---

