---
title: "My OOffice 2.2 panel buttons disappeared (!?) -please help"
date: 2007-08-13
forum: General Help
---

### Post by rniella on 2007-08-13
Hi there, I´m using a fresh install of Feisty (Gnome) for the last couple of weeks and all of a sudden the buttons (icons) on the menu panels on all of the OpenOffice aps.are gone.. (please check attached image) I´ve been looking around for the answer without luck.. I´ve played around with the options/view menu, changed them around, but nothing happens.  I´m not sure if it is relevant but I´m using a Geforce 6200 FX Nvidia card which works fine.. the computer is an AMD 2.8 GHz with 1 GB of RAM.  As an additional clue, I´ve created a new (dummy) user, logged in and OpenOffice works great with this new user, all the buttons are shown.. thanks in advanced !!!!  Best regards !

---

### Post by p_quarles on 2007-08-13
It looks like you're using the Tango icon set, which is why the buttons disappeared. To fix:
```
sudo apt-get install openoffice.org-style-tango
```
There are also OOo icon sets for Industrial, Crystal, etc., etc. You can find them all by searching in your package manager.

---

### Post by rniella on 2007-08-13
Thank you !!  it worked !!  however, right after I installed the style it did not do anyting different, I had to go and erase my .openoffice.org2 file on my home directory and then after that it worked OK, thanks !

---

