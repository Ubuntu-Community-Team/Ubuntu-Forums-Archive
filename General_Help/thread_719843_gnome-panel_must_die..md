---
title: "gnome-panel must die."
date: 2008-03-09
forum: General Help
---

### Post by vexorian on 2008-03-09
Some if not most WINE full screen directx apps cause gnome-panel to freak out when the resolution is changed, it scrabbles all my toolbar icons (Which then requires me to waste plenty of time reordering them correctly), and after many things I tried to prevent this, I came to the conclussion of killing gnome-panel.

So, what I do right now to kill gnome-panel is:

* system\pref\sessions\ Click gnome-panel's field, change from restart to normal.

* After that, pkill gnome-panel.

This works, the whole session thing is to prevent gnome-panel from being restarted. I was wondering if there is a command line to do that whole session giberish without having to do it manually. I could then make my scripts launching my beloved directx games be able to automatically kill and restore gnome-panel appropriately.

---

### Post by Oldsoldier2003 on 2008-03-09
> **vexorian said:**
> Some if not most WINE full screen directx apps cause gnome-panel to freak out when the resolution is changed, it scrabbles all my toolbar icons (Which then requires me to waste plenty of time reordering them correctly), and after many things I tried to prevent this, I came to the conclussion of killing gnome-panel.

So, what I do right now to kill gnome-panel is:

* system\pref\sessions\ Click gnome-panel's field, change from restart to normal.

* After that, pkill gnome-panel.

This works, the whole session thing is to prevent gnome-panel from being restarted. I was wondering if there is a command line to do that whole session giberish without having to do it manually. I could then make my scripts launching my beloved directx games be able to automatically kill and restore gnome-panel appropriately.
kill gdm and launch your games in their own xserver.


[http://gaming.gwos.org/doku.php/wine:winestuff#advanced_stuff](http://gaming.gwos.org/doku.php/wine:winestuff#advanced_stuff)

---

