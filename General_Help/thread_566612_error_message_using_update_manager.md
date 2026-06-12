---
title: "error message using update manager"
date: 2007-10-03
forum: General Help
---

### Post by d_iane1954 on 2007-10-03
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

i get this error message when trying to update via the update manager.i have a fresh download of ubuntu gamer 1.5 installed.when i enter the command in a terminal the reply is no such command.any and all help is greatly appreciated!!!!

---

### Post by d_iane1954 on 2007-10-03
it also says software index is broken?????? any help,thanks!!!

---

### Post by d_iane1954 on 2007-10-03
bump

---

### Post by rsambuca on 2007-10-03
Open a terminal and paste this into the terminal```
sudo apt-get install -f
```

And for future reference, it is considered very bad etiquette to bump your posts so quickly.

---

### Post by d_iane1954 on 2007-10-03
thank you for your reply and am sorry for the inconsideration i extend my apoligies.when i enter that in a terminal i get the following reply E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
when i run this im told i need superuser privelages for this task.dont really know what to do here.thanks very much for your attention to this problem.

---

### Post by drs305 on 2007-10-03
> **d_iane1954 said:**
> thank you for your reply and am sorry for the inconsideration i extend my apoligies.when i enter that in a terminal i get the following reply E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
when i run this im told i need superuser privelages for this task.dont really know what to do here.thanks very much for your attention to this problem.

sudo dpkg --configure -a

---

### Post by tecpatzin on 2007-10-08
thank you! drs305  your solution worked!

I was having the same issues but since I am very new to Ubuntu its alot to 
take in at one time. where would a newbie need to look for further info on getting to 
know Ubuntu better?

---

