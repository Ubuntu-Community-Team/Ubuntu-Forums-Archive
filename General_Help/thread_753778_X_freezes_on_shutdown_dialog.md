---
title: "X freezes on shutdown dialog"
date: 2008-04-13
forum: General Help
---

### Post by Intangir on 2008-04-13
i just installed gnome TONIGHT

i installed compiz/video drivers
i installed wine

everything still worked fine

i turned off a few session applets and services, and indexing
i removed a couple gnome-panel applets..

now when i press the 'Quit' button in top right, or goto System Quit. it stops responding
nothing in X/gnome/compiz moves, nothing responds, it doesnt open the quit dialog, and it doesnt quit

if i ctl-alt-backspace it closes and restarts, but nautilus doesnt

i cant quit from a logged in session, but if i ctl-alt-backspace, and quit from gdm, it works

---

### Post by Intangir on 2008-04-13
weird.. just now it worked

all ive done since is .. open firefox (which i doubt did it) and i opened the system->Preferences->Power Managment

i looked in there but nothing looked important, so i closed it without even changing anything

afterward it let me quit like normal.. maybe its fixed?

---

### Post by Intangir on 2008-04-13
its still broken

it is freezing up almost every single time

it freezes wether im running metacity or compiz

---

### Post by Intangir on 2008-04-14
i figured it out, apparently if you remove gnome-power-manager from your sessions startup.. you cant log out!

---

