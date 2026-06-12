---
title: "Screwed up my gnome panel"
date: 2007-04-02
forum: General Help
---

### Post by louisd11 on 2007-04-02
I was installing a program and one of the steps was to restart the gnome panel with a "kill all gnome" command or something like that. Well anyway when I did that when the screen came back to normal the battery meter I had was in a window. So I started trying to figure out how to get it back up their, but for some reason it wouldn't budge. So I started flicking with my other icons in the top right and then my GAIM icon went missing. SO how do I restore the battery meter icon back up their and the GAIM icon. Also in the mist off all of this now when I go to "show battery meter" in the System>Preferences>Power Management. I keep flicking on show meeter and hide meter but for some reason the meter totally disaperead. HELP PLEASE!!!

EDIT: Alsom many icons are missing. The only ones showing are the computer screen and the volume control. And when I open up aMule the icon shows in the top telf corner under the panel.

---

### Post by zvacet on 2007-04-03
It was probably refresh gnom panel and command is
```
killall gnome-panel
```

and command you are looking for is 
```
sudo /etc/init.d/gdm restart
```

---

### Post by louisd11 on 2007-04-03
It didn't work but this command did 

> rm -rf .gnome .gnome2 .gconf .gconfd .metacity

Thanx for your help anyway

---

