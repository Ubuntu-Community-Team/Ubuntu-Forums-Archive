---
title: "diagnostic start-up"
date: 2008-06-19
forum: General Help
---

### Post by L0c on 2008-06-19
is there a way to permanetly make boot-up in text mode?
i'm not sure if i was clear so i'll explain
currently(default) kubuntu(doesnt really matter taht it's kubuntu) boots with that progress bar. the way i would like it that it prints out on a text screen(or some kind of hybrid with the progress bar) current operation and if it is success or not.

i remember i found it before for an older version of ubuntu, but i cant find those instructions online anymore...

even better if there is a way to get a hybrid which has both progress bar and text on a part of screen(you know, fancy looking :D )

---

### Post by ktrnka on 2008-06-19
If you want to see only text with out the boot splash screen

```
sudo nano /boot/grub/menu.lst
```
Scroll down to the bottom and you should see something similar to

title             Ubuntu 8.04
root         (hd0,1)
kernel       /boot/vm.................. ro quiet splash

If you remove the quiet and splash, you will see the text only.

If you are looking for a hybrid, I would suggest installing startupmanager heading over to gnome-look.org for one displays both. Then all you would need to do is remove quiet and your bootup splash will display both. 

Something like this
[http://gnome-look.org/content/show.php/Usplash+ubuntuclub2?content=37496]("http://gnome-look.org/content/show.php/Usplash+ubuntuclub2?content=37496")
 right?

---

