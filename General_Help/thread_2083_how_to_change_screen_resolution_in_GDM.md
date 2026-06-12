---
title: "how to change screen resolution in GDM"
date: 2004-10-25
forum: General Help
---

### Post by tanari on 2004-10-25
how to change screen resolution in GDM?
I have 1920x1440 in GDM, and 1152x864 on desktop.

---

### Post by JProgrammer on 2004-10-25
When you set the resolution in Gnome it doesn't change anything in your X configuration. to change GDM you need to edit /etc/X11/XF86Config-4 look for the resolutions section and just delete all resolutions before 1152x864 or if you want to access these other resolutions still just move that to the frount. It is most important to move it in the 24 bit secition since I would assume you are running it at this resolution.

sudo vim /etc/X11/XF86Config-4
or
sudo gedit /etc/X11/XF86Config-4

---

