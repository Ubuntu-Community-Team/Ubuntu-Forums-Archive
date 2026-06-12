---
title: "[SOLVED] Unable to delete Wine application entries"
date: 2008-06-01
forum: General Help
---

### Post by pmaconi on 2008-06-01
I posted this in the Wine forum also, but I'm not sure if it is a Wine problem or a Gnome problem. 

I recently attempted to install iTunes in Wine. After seeing that it wasn't working correctly, I tried to uninstall it via the Wine add/remove programs gui. It said that the uninstall was successful, but the launcher entries remained under Applications -> Wine.

I removed my ~/.wine folder and completely reinstalled wine, hoping to get rid of them. No such luck. They just moved to Applications -> Other. I can't edit the menu and delete them through that (I tried, but it doesn't do anything). I also don't see them in the ~/.config menu file. Does anyone know any other way to delete the entries?

Thanks!

---

### Post by ibuclaw on 2008-06-01
Press "**Alt+F2**" to open up the Run App bar and copy in:
```
nautilus ~/.local/share/applications/wine
```
All your wine menu entries are in that folder.

Regards
Iain

---

### Post by disturbedite on 2008-06-01
i had this problem in kde3 as well.  i found no solution that worked, and i read about quite a few possibilities.  i resorted to uninstalling wine completely (including manually deleting the menu entries) & then reinstalling wine, which fixed the problem.

---

### Post by pmaconi on 2008-06-02
Thanks tinivole, that did the trick.

---

### Post by djdarrin91 on 2008-06-02
tinivole that worked perfect for me as well, thank you!

---

### Post by ache109 on 2008-06-12
hey tinivole.. it works!!

---

### Post by quazzimodo on 2008-12-19
Thanks Tinivole worked for me too

---

### Post by reahjw6 on 2009-01-01
Thanks this relly helped.

---

### Post by Slavko.M on 2009-07-22
Thanks tinivole... It also worked for me... UBUNTU 9.04
"May the force be with you..."

---

### Post by inearlygaveup on 2009-10-20
Thanks tinivole... It also worked for me... Intrepid Ibex

---

