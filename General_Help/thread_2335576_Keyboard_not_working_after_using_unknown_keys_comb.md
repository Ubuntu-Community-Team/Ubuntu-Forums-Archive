---
title: "Keyboard not working after using unknown keys combination"
date: 2016-08-30
forum: General Help
---

### Post by soxterix on 2016-08-30
Sometimes my fingers slip while typing special characters  (I probably use ALT or/and CTRL or/and SHIFT and some kind of a letter) keyboard turns off and I'm not able to write anything in any application, I also can not use Menu Bar (**using mouse**) of any application (for example close it by clicking X button). Basicly the only thing I can do is restart/turn off computer from Ubuntu menu bar which works. Everythings works fine after restart. I would like to know what keys combination I use and how to turn it off while it happens. Any ideas?

BTW, I use Ubuntu 14.04.

---

### Post by Jimysbil on 2016-08-30
My theory is that some button (or button combination) could partly crash your GUI.
Maybe when this happens you could use CTL+ALT+F1 combination in order to get you in terminal.After that log in with your account and type:
```
sudo service lightdm stop
```
* This command will stop your Graphical interface.
By typing:
```
sudo service lightdm start
```
** This command should restart your GUI.

---

### Post by soxterix on 2016-08-30
Thanks for the suggestion, I'm going to try your solution when it happens again.

---

