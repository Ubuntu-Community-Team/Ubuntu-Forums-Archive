---
title: "gdesklet .. always on top"
date: 2006-11-18
forum: General Help
---

### Post by maneesh on 2006-11-18
Hi folks, I want to keep some of my desklets always on top, e.g. starterbar..  I want to keep this desklet always on the top so that I can click on anytime even when my dominating window is on maximized. If not this, then can it behave like gnome-panel, which actually restricts the window resize ???

Thanks

---

### Post by bigken on 2006-11-18
i think if you right click the desklet it gives the option always on top ;)

---

### Post by maneesh on 2006-11-26
No atleast the desklet-starterbar doesnt show up that option on right click :(.. I did see this option in a couple of desklets though.

---

### Post by saviokzam on 2008-05-19
Yes, it's possible to start and keep the starter bar always on top. Just open with root privilege the file "starterbar.display". Open a terminal and write:

# sudo gedit /usr/share/gdesklets/Displays/starterbar-desklet/starterbar.display (if you installed in default directory)

On tag "display", change window-flags="below, sticky" to window-flags="above, sticky"

And now restart starterbar. That's all.

Regards,

Savio Kzam.

---

