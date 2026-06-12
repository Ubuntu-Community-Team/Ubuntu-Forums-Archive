---
title: "my terminal window transparency ain't cool"
date: 2008-05-12
forum: General Help
---

### Post by superpink99 on 2008-05-12
i tried to make my terminal window transparent, the problem was that, it was transparent but what i wanted was that when two open windows are on top of each other you should still see the other one on the buttom and NOT the desktop background. how do i make my ubuntu skins transparent anyway?

---

### Post by hermes0710 on 2008-05-12
You could disable the transparency on your terminal and manage opacity through Compiz Settings (General options,windows opacity).

---

### Post by Canis familiaris on 2008-05-12
You have to Enable Desktop Effects i.e. compiz and then it will show the window underneath.

---

### Post by superpink99 on 2008-05-12
guys how do i manage opacity with compiz? please im really new to ubuntu, come on please give me a break i just installed this OS 3 days ago.

---

### Post by tjwoosta on 2008-05-12
first you would have to enable compiz by going to System-Preferences-Appearance  click the visual effects tab then click extra

then you have to install compiz config settings manager (go to add/remove and search compiz, it should be like the first one in the list)

then go to System-Preferences-Advanced Desktop Effects Settings and go to General Options and click the opacity settings tab

this is where it gets hard to explain (i will just give you a copy of my settings) 
just click new at the bottom and paste this into the opacity windows box
```
type=normal & ! title=Mozilla & ! state=fullscreen & ! title=npviewer & ! title=GNOME & ! title=Google & ! role=gimp-image-window & ! title=Miro & ! name=evince & ! name=opera
```

this will make most windows see-thru but keep firefox and opera and GNOME MPlayer and google earth and some others regular

basically if you want everything to be see-thru you would only need this part
```
type=normal
```
(the & ! means and not)

also for menus and stuff make a new one and put this in the opacity windows box
```
Tooltip | Menu | PopupMenu | DropdownMenu
```

(remember when setting opacities for both of theese things to make sure you dont set it too low because then it becomes invisible and you will have to reboot in safemode to fix things)

---

### Post by TWeerts on 2008-05-18
i just tried this, and my advanced desktop settings box disapeared. i cant see it at all. now i cant change anything. help?

---

### Post by DrDeo on 2008-06-11
[http://www.ubuntugeek.com/howto-create-a-transparent-terminal-in-ubuntu-desktop.html](http://www.ubuntugeek.com/howto-create-a-transparent-terminal-in-ubuntu-desktop.html)

much simpler way for the uninitiated.

---

### Post by Nythain on 2008-06-11
seriously, do you use gnome-terminal, because by default compiz is usually on (at least if you have the proprietary drivers installed) and gnome-terminal supports real transparency with a compisitor (compiz)... i didnt have to tweak anything, just enabled desktop effects and told gnome-terminal to be transparent, and voilla, real transparency and not pixmap pseudo-transparency

---

### Post by ample on 2008-07-25
> **Nythain said:**
> i didnt have to tweak anything, just enabled desktop effects and told gnome-terminal to be transparent, and voilla, real transparency and not pixmap pseudo-transparency

you say you told gnome-terminal to be transparent, does that mean the usual Edit->Current Profile->Effects tab->transparent background? cause i still get the pixmap pseudo-transparency, which is not what i want.

-ample

---

