---
title: "How do you run programs at login screen?"
date: 2008-05-04
forum: General Help
---

### Post by Christian Christiansen on 2008-05-04
I want to run a program when I get to the login screen (GDM). I heard something about adding "exec program &" to /etc/gdm/Init/Default but that didn't work for me. 

Any other ideas?

By program I mean onscreen or cairo-clock

---

### Post by NightwishFan on 2008-05-04
I am not sure if that could work but then again I never tried it. :popcorn:

---

### Post by Christian Christiansen on 2008-05-04
Sorry, found out it didn't work because I didn't have onscreen installed. I'm really happy now because I've got compiz fusion running on the gdm with gnome-panel. It's amazing.

---

### Post by ghost_ryder35 on 2008-05-04
congrats.  maybe you could post what you did on this thread so future people searching for the same thing could easily locate it?  Thanks

---

### Post by Christian Christiansen on 2008-05-04
to do what I did first you need to get compiz running

then 
"sudo cp /etc/gdm/Init/Default /etc/gdm/Init/Default.backup"
This makes a backup of your current gdm settings so it will be easy to restore if anything goes wrong.
Then
"sudo gedit /etc/gdm/Init/Default"
The add this before "exit 0"
"exec compiz &"
"exec emerald &" OR "exec metacity &" 
"exec gnome-terminal &"
You can also put other stuff in but I prefer to stick with these settings. Hope this helps

---

