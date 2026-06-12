---
title: "NVIDIA driver install - kill X server"
date: 2005-05-15
forum: General Help
---

### Post by hammett111 on 2005-05-15
New recruit from the world of microsoft!! 

I need help. I have the latest drivers from Nvidia for my vid card, however I can't install until I kill X server. How do I do this?

Also I would like to boot straight from a vga console, utilising my new drivers and vid card and bypassing x server. How do I do this.

Cheers

---

### Post by Juippisi on 2005-05-15
> 
I need help. I have the latest drivers from Nvidia for my vid card, however I can't install until I kill X server. How do I do this?


Try pressing Ctrl+Alt+F1, then login and type "sudo killall gdm". That should be enough. When you want to login back to Gnome, type "sudo /etc/init.d/gdm" or 
"sudo /etc/init.d/gdm start" (I don't remember, I don't personally use graphical login managers).



> 
Also I would like to boot straight from a vga console, utilising my new drivers and vid card and bypassing x server. How do I do this.


If I got this right, you need to edit menu.lst (/boot/grub/menu.lst) and put some options to the kernel which you are booting. I don't know those options, sorry. Sorry for my bad english as well :\.

---

### Post by hammett111 on 2005-05-15
Cheers bud, keep them rolling people, make me a linux convert

---

