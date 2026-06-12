---
title: "gDesklets"
date: 2007-01-10
forum: General Help
---

### Post by mevets on 2007-01-10
I tried to ad a gnome taskbar in gDesklets. Prolem is I cant plant it anywhere cause I keep being forced to open the first window on my taskbar I am dragging around.  I restarted to get rid of the problem and when I started up it lauched all my desklets again. I tried reinstalling but did not better my situation.

Is there an ini file or equailvalent so I can make sure that one desklet that causes problems not to launch?

---

### Post by MrJackdaw on 2007-01-17
Try stripping out Gdesklets completely. After using synaptic type sudo apt-get autoremove at the terminal. Then reinstall GDesklets. May work. May not :)

---

### Post by murlosad on 2007-01-17
You may also want to try just removing the .gdesklets directory from your home directory

~/.gdesklets

That is where gdesklets stores most of the settings for which desklets to open at start.

if MrJackdaw's suggestion doesn't work.

---

