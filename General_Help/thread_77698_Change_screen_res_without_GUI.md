---
title: "Change screen res without GUI"
date: 2005-10-17
forum: General Help
---

### Post by Nashy on 2005-10-17
When the GUI loads, my crappy monitorin the office (not main monitor) won't support the screen res.

Can I change it?  Please say yes.

---

### Post by Pablo_Escobar on 2005-10-17
Login,
type "sudo nano /etc/X11/xorg.conf"
then look for a line called DefaultDepth (or something like it)
If it says 24, a little lower You'll find subsection with 24. 
Erase in that section the higher resolution, leave only the desired.
CTRL + O , then CTRL + X, and startx :)

---

### Post by Nashy on 2005-10-17
It just opened a new file for editing :-(  More help?

---

### Post by Pablo_Escobar on 2005-10-17
try : 
"sudo dpkg-reconfigure xserver-xorg" - and choose only Your resolution

---

