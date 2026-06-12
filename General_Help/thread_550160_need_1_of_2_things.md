---
title: "need 1 of 2 things"
date: 2007-09-13
forum: General Help
---

### Post by yon2501 on 2007-09-13
ok i need to know 1 of two things here i use crossover linux and im trying to install a game from disc i need to know how to eject a disc so i can insert the second disc one to finish the install, whenever i try it says cannot eject disc because it is in use, so what i need to know is 1 how to eject discs for this kind of thing or 2 how to mount an iso and do it that way

---

### Post by tszanon on 2007-09-13
I guess you're using the terminal for all this, right? You can't eject the cd if you're currently inside its directories. Example:
the cd is mounted in /cdrom. If I'm currently inside /cdrom, then I can't eject the cd until I leave it:
```
cd /
```
I think that's your case. But I'm not sure, since I never used Crossover.

---

### Post by leonidas666 on 2007-09-13
If you want to find out which process exactly is occupying the cdrom you can use the following command:
sudo lsof | grep cdrom

lsof lists all open files, and with the grep it will only display lines in which "cdrom" appears. If your cdrom is mounted in a different directory you should use that other directory's name.

---

### Post by yon2501 on 2007-09-13
well the thing is its running install wizard and it asks me to insert disc 2 to finish the install but when i try to eject it says its in use, i dont have anything but install wizard open, its a windows game thats why im using crossover linux

---

