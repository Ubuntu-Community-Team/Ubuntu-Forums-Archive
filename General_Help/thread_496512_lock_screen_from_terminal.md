---
title: "lock screen from terminal"
date: 2007-07-09
forum: General Help
---

### Post by kboykowboy on 2007-07-09
hey all - i have a crazy question. 

Anyone knows if you can lock the screen from the terminal?! in stead of going to apps., settings, screen saver, file, lock screen now... phuuu long way - right?!

K

---

### Post by smoker on 2007-07-09
ctrl+alt+L will lock your desktop in ubuntu:-)

---

### Post by kboykowboy on 2007-07-09
hmm... nothing happens here?! i have a danish iinstallation - could that be a problem?! or could the installation of opera have anything to do with it? it uses ctrl alt L  as a short cut... to something useless...

---

### Post by smoker on 2007-07-09
are you trying it on the desktop? i don't use opera, so don't know if that will make a difference.

---

### Post by diafanos on 2007-07-09
> **kboykowboy said:**
> hey all - i have a crazy question. 

Anyone knows if you can lock the screen from the terminal?! in stead of going to apps., settings, screen saver, file, lock screen now... phuuu long way - right?!

K

Why not Quit... -> Lock Screen

---

### Post by girishv on 2007-07-09
gnome-screensaver-command --lock

Girish

---

### Post by kboykowboy on 2007-07-09
girish - that worked! but now i have installed a new screensaver then... would be cool if it worked on the standard xubuntu install...

quit - lock screen is not an option on my ubuntu... probably also why ctrl-alt-L is not working?!..

---

### Post by smoker on 2007-07-09
> **kboykowboy said:**
> girish - that worked! but now i have installed a new screensaver then... would be cool if it worked on the standard xubuntu install...

quit - lock screen is not an option on my ubuntu... probably also why ctrl-alt-L is not working?!..

ctrl+alt+L works in gnome in ubuntu, if you are using xubuntu it will probably be something else!

---

### Post by kboykowboy on 2007-07-09
ok - i found something... quit suspend does it... i guess it is my pore english that made me miss that in the first place...

---

### Post by marsbt on 2007-07-09
But Suspend does not lock the screen. It makes the computer go into Suspend state. If you are using KDE, the command to lock your screen is *kdesktop_lock* (use -forcelock if you don't have password lock enabled for screensaver).

---

