---
title: "Problem concerning opacity"
date: 2008-06-27
forum: General Help
---

### Post by michaelgulak on 2008-06-27
I have compiz-fusion installed, and I have things like the desktop cube enabled.  I have a transparency effect for menus using (under the Opacity Settings tab of General Settings in the Advanced Desktop Effects Settings) Menu | PopupMenu | DropdownMenu at opacity 90.  This works fine, except in programs that I write that use the 3D library Ogre.  If I fullscreen the App, it's transparent as well - and that looks weird.  Has anyone had this problem before?  Removing "| DropdownMenu" from the opacity settings solves the problem, but it also gets rid of my opacity for my dropdown menus.  It's no big deal if I can't solve it, I am just curious.

---

### Post by Forlong on 2008-06-27
You can make an exception for that type of application.
For example this would make all windows transparent except for Firefox:
```
type=Normal & !(class=Firefox)
```

Hope this helps.
Don't hesitate to ask if you have any further questions.

---

### Post by michaelgulak on 2008-06-27
Hmm...  It'd be far more effective if I could just make it exempt the active window.  That's fine, though, it's really no big deal.  I'll run my programs windowed for the time being. :)

---

### Post by Cresho on 2008-06-30
i have a question

I am running compiz-fusion with xpmc (xbox media center-gtk based and done for free also open source).  I have opacity windows setup like this

Tooltip | Menu | PopupMenu | DropdownMenu


It's fine and all.  When I launch xpmc, it is fully maximized but when I hit the "\" key (this maximizes it). it is transparent at 85 just like the others.  What is rendering it?  how do I add a command to prevent it from going transparent at full screen.  I must of spent 4 hours today looking for an answer and now I am reffering the the forums.

---

### Post by Cresho on 2008-07-02
i fixed opacity problem by disabling the workaround in compizconfig

---

