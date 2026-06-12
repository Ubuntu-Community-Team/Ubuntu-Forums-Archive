---
title: "Global menu + certain applications menu bars show duplicate entries. (i.e. kdenlive)"
date: 2016-01-27
forum: General Help
---

### Post by Roasted on 2016-01-27
Hi friends. I often run Kdenlive on Ubuntu. One thing I've been questioning on a continual basis is whether or not it's possible to disable Kdenlive's menu bar where File, Edit, etc are located. Reason being is here in Ubuntu, we have a global menu. But this ends up duplicating the entries in the menu bar, so I see two Files, two Edits, etc. It just looks... a bit strange. Any ideas on how I can disable one or the other? I went through Kdenlive's settings but did not see anything for this particular menu bar.

[[img]http://s6.postimg.org/pus0y8yv1/kdenlive_unity.jpg[/img]](http://postimg.org/image/pus0y8yv1/)

---

### Post by Roasted on 2016-01-29
No idea? :(

---

### Post by howefield on 2016-01-29
Thought I'd take a look before wasting this install, but no joy short of Ctrl + Shift + F (full screen mode)

---

### Post by Roasted on 2016-01-29
Yeah - I noticed that too. On one hand, I enjoy keeping Kdenlive in another workspace (along with a 50% screen right-justified file manager open) with Kdenlive maximized. This allows for a quick alt+tab to be within my files where I can drag/drop additional clips into the Kdenlive workspace, which by default is located on the left side of Kdenlive. Then of course the usual workspace switcher shortcuts if I need to go back to any main stuff I may have open.

That workflow admittedly works well. But it just seems a bit strange if you're not in this kind of workflow that duplicate entries exist. It'd be nice if that was customizable. To date Kdenlive is the only application that acted this way, so I suppose I should take it as a good sign, but it'd just be nice if it could be altered a bit... just that little checkbox to disable the main menu, or even bury the entire main menu into a Firefox/Chrome esque "3 horizontal line" menu to at least get it out of sight.

Eh, anyways - figured I'd ask. Thanks for checking howefield!

---

### Post by rg4w on 2016-01-29
It may be an easy-to-fix bug in the app.  My (admittedly limited) understanding of how the global menu bar works is that when an app defines its menus using the standard Qt or GTK methods, Unity will automatically take care of exporting the menu definitions to the global menu bar, cropping the content region as well so the menus are only in one place.  

Here we see KdenLive having its menus exported fine, but not in a way that Unity can crop them from the window's content region.  Given this, my hunch is that all that's needed is a minor adjustment to how the menus are set up, and once in place the app would appear fine in Ubuntu. 

Probably worth filing a bug report on with the KdenLive team to at least see what they say.

---

