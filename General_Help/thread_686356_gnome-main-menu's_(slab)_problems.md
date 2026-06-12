---
title: "gnome-main-menu's (slab) problems"
date: 2008-02-03
forum: General Help
---

### Post by wersdaluv on 2008-02-03
I attached a screenshot of the Places component of my gnome-main-menu. I have a few bookmarks and they're not displayed well in the menu. For example, my GTD folder is named GTD GTD. Whenever I open it, an error message will say "Couldn't find "/GTD"." That's probably because the name is doubled. How can I fix this?

Also, do you guys know where I can find the configuration files?

Last, my gnome-main-menu, for some reason, is now occupying a larger portion of the screen. How can I put it back to its old size?

Thanks in advance!

:KS

---

### Post by mariner09 on 2008-04-09
It looks like you edited your config xml files that are located in /usr/share/gnome-main-menu.

There is a file called places.xbel.  Look at the format for the proper entries and then look at the entries that have double names.  Looks like they think the path is /GTD while it should at least be ~/GTD or something like that.  I don't think that the main-menu recognizes ~ as a path reference to your home directory.  You may need to add the full path.

Open gconf editor and look at desktop/applications/main-menu/file-area.  This has a setting for max total items and you can change that to a number like 6.

---

