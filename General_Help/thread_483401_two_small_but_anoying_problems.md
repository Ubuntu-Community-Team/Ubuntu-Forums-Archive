---
title: "two small but anoying problems"
date: 2007-06-24
forum: General Help
---

### Post by Sjovan on 2007-06-24
Hey, I need help with two small problems. 
1. how to get a mounted device (in this case hdb1) away from the desktop.
2. how to move all the small in the games on the main menu into a folder \games\mini games

1. problem
in /etc/fstab
```

# /dev/sdb1
UUID=3afa9a64-48fe-4d86-b05f-dd63beecb43f /media/Music    ext3    defaults        0       0
```
Something i can do with the code? I have tryed two mount it in /mnt/ and with 0           2, but the only difference is that it says /mnt/Music instead of just Music on the desktop.
So how can i fix this problem?


2. problem
I have created the folder /games/mini games in the main menu by right-clicking--->edit menus, but it is inpossible to drag the files into that folder. Okay, I Can just uncheckall te games and add icon, name and location manualy in the folder, but it has to be a easyer way. Is there maby a file that i could just add a little /mini\ games/ to the location on every game or something?


Thanks in advance
Karl Isak

---

### Post by yabbadabbadont on 2007-06-24
1) You can either have all mounted hard drive parititions on the desktop or none of them.  I don't believe that Gnome gives you any other option.  You'll need to run the gconf-editor and then navigate to the nautilus settings.  There is a setting that is something like "volumes visible" that you can change.

---

### Post by Sjovan on 2007-06-25
Tanks alot yabbadabbadont.

gconf-editor

/apps/nautilus/desktop and uncheck volumes_visible did the trick.

---

