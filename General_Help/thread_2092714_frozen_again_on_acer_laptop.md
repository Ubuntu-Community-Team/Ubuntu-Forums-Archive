---
title: "frozen again on acer laptop"
date: 2012-12-08
forum: General Help
---

### Post by stephenbbb on 2012-12-08
I have an acer 5250 laptop with ubuntu 12.04 default unity desktop. the desktop GUI is frozen again and the system is unusable. second time it happens. going into recovery and previous versions does nothing. only a more radical update of the version will cure it and I do not want to wait 3 months.

finally the question: is there a more stable desktop I can switch to? if I drop to root from the recovery the os is usable, but starting the desktop goes to freezing. 

thanks everybody.

---

### Post by black veils on 2012-12-09
you say you think a system/desktop upgrade will cure it, so what do you think is wrong?

go to software centre and install:

[B]xfce4
xfce4-goodies[/B]

its just the base environment i think, if you want the full xfce desktop as customised by the Xubuntu team (part of ubuntu family) then:

[B]xubuntu-desktop
xfce4-goodies[/B]

everything you see can be changed.

---

### Post by stephenbbb on 2012-12-10
sth goes wrong with the desktop which is driven by X. since the whole thing is totally frozen I cannot use any of the usual to report a problem. from root I can access all logs, but so far have not found anybody interested in solving this.
from root I can start xinit and even run many graphical apps from the terminal. anyway it is still very inconvenient.

btw is KUbuntu a separate desktop or a separate os?

---

### Post by dragonfly41 on 2012-12-10
I'm running Ubuntu 12.04 on an old Acer laptop.

Perhaps as one option to try install [COLOR=Blue]gnome-session-fallback[/COLOR] and reboot to login to the gnome classic session.

At login point you need to select the desktop session from a menu (e.g. Unity or Classic Gnome).

---

