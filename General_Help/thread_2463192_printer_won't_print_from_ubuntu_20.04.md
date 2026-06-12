---
title: "printer won't print from ubuntu 20.04"
date: 2021-06-05
forum: General Help
---

### Post by jaxom98 on 2021-06-05
Not sure if I am in the right place
.
PC, dual booted with win 10 and ubuntu 20.04  
printer, HP office jet pro 8710 with wired connection to PC

 In win 10 the printer works
In ubuntu 20.04 the printer won't. 
In settings the printer shows.  It seems to be trying to print to file. I want send the file to be printed, but the window shows print to file only.
 I tried to delete the printer, and start again, but it won't delete.  I click on remove printer, and it vanishes with an "undo" window appearing, then after about 10 seconds the "undo" window times out and the printer reappears in the printer list.

This printer was working on a wired  dual boot PC with ubuntu 16.04 and win 7, and once the cups codec was sorted(ubuntu), worked textbook perfect,  I had to change the PC as the old mobo died

---

### Post by dukesilver1701 on 2021-06-07
I have had the same issue and have found using hp-lip software corrects my same problems. See below link 

[https://developers.hp.com/hp-linux-imaging-and-printing](https://developers.hp.com/hp-linux-imaging-and-printing)

---

### Post by jaxom98 on 2021-06-11
Excuse the delay in reply. I am a beginner and don't know how to apply this.

---

### Post by kc1di on 2021-06-11
It may be helpful to install hplip-gui you can do that in a terminal with this command ```
sudo apt install hplip-gui
``` once installed go to the menu and do a search for hp and you'll either hp device manager or hp tool box. click on that program and follow the instructions for adding your printer. 
Good luck

---

