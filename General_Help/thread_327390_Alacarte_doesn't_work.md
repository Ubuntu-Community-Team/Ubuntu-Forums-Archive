---
title: "Alacarte doesn't work"
date: 2006-12-29
forum: General Help
---

### Post by lift_test on 2006-12-29
Loaded new programs but don't show in menu.  Tried to add unticked groups (Other - Debian) in case the programs were classified under these headings.  When run from menu it will not tick these two items.
If run from terminal "sudo alacarte" it runs with the same result but there is an error mesage "ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave"  

Any ideas what this means and what can be done to correct it?  

I did think of trying to uninstall/reinstall alacarte but a wrning message said that the Gnome desktop would have to be removed, I wimped out at that point as I would probably have to reinstall to get the desktop back!
Thanks in anticipation.](*,)

---

### Post by ThrobbingBrain66 on 2006-12-29
ubuntu-desktop is just a meta-package, so the WHOLE desktop wouldn't have been uninstalled, but it is a tricky thing the first time you see it. :)

What packages did you install?  Most add a menu item, but some don't (especially if they are command line packages).

---

### Post by lift_test on 2006-12-29
Real Player and Eagle PCB drawing program, neither are command line programs.  My original question still stands "why doesn't Alacarte work?"

---

### Post by ThrobbingBrain66 on 2006-12-29
> **lift_test said:**
> Real Player and Eagle PCB drawing program, neither are command line programs.  My original question still stands "why doesn't Alacarte work?"

Have you logged out and logged back in?  Sometimes the menus don't update until after a logout.  If this doesn't fix them problem, all we have to do is know the command for the packages and we can create our own menu shortcuts.  There's a good chance that it's not just alacarte "not working", it may just be that the packages don't make a menu item

---

### Post by anaconda on 2006-12-29
> **ThrobbingBrain66 said:**
>  it may just be that the packages don't make a menu item

I agree. Many programs just dont add themselves to the menu, and you have to do it manually. BY going to alacarte and selecting the place you vant to add your menu item, and select add.

---

