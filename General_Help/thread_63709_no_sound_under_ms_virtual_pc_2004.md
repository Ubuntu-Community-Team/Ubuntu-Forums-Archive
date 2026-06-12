---
title: "no sound under ms virtual pc 2004"
date: 2005-09-08
forum: General Help
---

### Post by fraildog on 2005-09-08
hi there, can anyone tell me the settings i need to alter for hoary ubuntu, I have no sound!

Thankya!

R

---

### Post by fraildog on 2005-09-08
To get sound working add "snd-sb16" to /etc/modules 
Lindley Lee added detailed instructions:

Log into another virtual session as root 
# cd /etc/X11 
# pico xorg.conf (to edit xorg.conf) 
Now, scroll down in pico to Section "Screen" and find the entry
named "DefaultDepth". Change the setting you find there from 24 to 16. 
Ctrl O 
Enter 
Ctrl X 
# reboot 


copied from another website! apologies
fraildog

---

### Post by fraildog on 2005-09-08
To get sound working add "snd-sb16" to /etc/modules

---

