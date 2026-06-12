---
title: "Window decorator is missing (border, icons)"
date: 2015-03-09
forum: General Help
---

### Post by hipi on 2015-03-09
Hi,
I have a recently installed 14.10 Ubuntu 64bit, and window decorators are missing on all Nautilus window. How can I restore them?
I tried resetting Unity, but no success.
I have no problems with other applications (e.g. Firefox), but Nautilus windows are affected and it is very annoying that icons are missing.
Thank you for you help in advance.

[ATTACH=CONFIG]260539[/ATTACH]

---

### Post by ajgreeny on 2015-03-09
You probably need to install **compiz config settings manager (ccsm)** if it's not already installed and make sure that the window-decoration plugin is enabled.
I assume you are aware of the fact that global-menus, and icons for close, minimize & maximize are mostly now in the top panel, not the window decoration titlebar; put your cursor in the top panel and the menus etc for the active window appear there.

---

### Post by mc4man on 2015-03-09
You're getting the nautilus that is used in a gnome session, not in an ubuntu session.

Why, no idea, maybe you aren't in an ubuntu session or used ubuntu-gnome iso or something else you did.

for starters, run this in a terminal, (ctrl+alt+t),  what does it report
```
echo $DESKTOP_SESSION
```

---

### Post by hipi on 2015-03-09
mc4man:
I am in ubuntu session:

```
hipi@desktop:~$ echo $DESKTOP_SESSION
ubuntu
```

---

### Post by hipi on 2015-03-09
> **ajgreeny said:**
> You probably need to install **compiz config settings manager (ccsm)** if it's not already installed and make sure that the window-decoration plugin is enabled.
I assume you are aware of the fact that global-menus, and icons for close, minimize & maximize are mostly now in the top panel, not the window decoration titlebar; put your cursor in the top panel and the menus etc for the active window appear there.

When I try to enable Window Decoration in CCSM I got the following:
"Plugin Ubuntu Unity Plugin provides feature decorations which is also provided by Window Decoration"
[ATTACH=CONFIG]260543[/ATTACH]

---

### Post by mc4man on 2015-03-09
Maybe try  - 
r. click on Desktop > Change Desktop Background > in the theme drop down switch to high contrast, then back to Ambiance. Then log out/in. Any change?

---

### Post by hipi on 2015-03-09
No.

But I finally found the solution!
I reverted the Gnome3 changes as can be seen here: [http://www.webupd8.org/2014/10/how-to-install-gnome-314-in-ubuntu.html](http://www.webupd8.org/2014/10/how-to-install-gnome-314-in-ubuntu.html)
Missing icons and borders was caused because it. I reverted the gnome3 ppa, and now everything is okay again in Nautilus.
Thank you for your idea and your help!

---

### Post by mc4man on 2015-03-09
> **hipi said:**
> No.

But I finally found the solution!
I reverted the Gnome3 changes as can be seen here: [http://www.webupd8.org/2014/10/how-to-install-gnome-314-in-ubuntu.html](http://www.webupd8.org/2014/10/how-to-install-gnome-314-in-ubuntu.html)
Missing icons and borders was caused because it. I reverted the gnome3 ppa, and now everything is okay again in Nautilus.
Thank you for your idea and your help!
Well using that ppa would do it as Ubuntu patches/configures nautilus to work/look correctly in an ubuntu session. The ppa doesn't as it's more for users that want to use a gnome session (gnome-shell

---

### Post by CantankRus on 2015-03-09
Amuses me how people don't think adding the GNOME 3 Staging PPA relates to problems 
they are having and don't include this info in the original post. :roll:

When you install the ppa this warning shows before you press "Enter" to allow ...
```
=== *WARNING* ===
The packages here have been deemed not ready for general use, they have known bugs and/or regressions, sometimes of a critical nature. Mostly things should run smoothly but be prepared to use ppa-purge, when you encounter issues!

If they break your system, you get to keep both halves.
```

All the web guides I've seen offer similar warnings.

---

