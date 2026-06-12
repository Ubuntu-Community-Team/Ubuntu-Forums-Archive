---
title: "That menu editor"
date: 2006-11-09
forum: General Help
---

### Post by Mr. Picklesworth on 2006-11-09
This is about the menu editor for Ubuntu Edgy (Gnome), in System -> Preferences -> Menu Layout.

Is there a better one?
Is there an effort / feature request to improve it?

I'm having the following problem with it:
I have a program which dumped a whole ton of useful items on my Programming menu. Unfortunately, I like menus that are tidy, so I want to move these to a sub-menu. It is, unfortunately, impossible to do this with drag & drop!

To cap that, I find the current menu editor slow and that it often requires me to log out and in to see my changes (though that may be something else's fault, so I'm not considering it really horrible).

All in all, I unfortunately do not like it.
So, do you know of alternatives?

---

### Post by CatKiller on 2006-11-09
> **Mr. Picklesworth said:**
> To cap that, I find the current menu editor slow and that it often requires me to log out and in to see my changes (though that may be something else's fault, so I'm not considering it really horrible).

I haven't used Edgy much, but in Dapper at least you can run **killall gnome-panel** as a quicker alternative to logging out and back in. Sorry I can't help you with your other issues.

EDIT: It's not like you even create sub-menus in Dapper by drag-n-drop. It's all about the File -> New Menu. Perhaps they've kept it the same in the Edgy application? I'm not near my Edgy install at the moment, so I can't check.

---

### Post by Mr. Picklesworth on 2006-11-09
Oh, the submenus are created easily; it's just moving already existing items between menus that is difficult.

---

### Post by CatKiller on 2006-11-09
> **Mr. Picklesworth said:**
> Oh, the submenus are created easily; it's just moving already existing items between menus that is difficult.

That's true. I'm on the Edgy computer now, so I got a chance to try it. It **seems** to be behaving the same as the Dapper one, in that you can pick up the menu items and drop them in another menu, and then the focus switches to the new menu. It's just that the entry doesn't get moved for some reason. Sounds like an oversight to me, and hopefully one that will be fixed.

In the meantime, you **could** edit the ~/.config/menus/applications.menu directly, although I don't think I'd recommend it.

---

### Post by hikaricore on 2006-11-09
One thing I've noticed is that menu items without spaces or special characters can be easily moved and then later renamed.  This is a horridly annoying way to do it but it works for me. :/

---

