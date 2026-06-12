---
title: "can't install fluxbox"
date: 2008-04-25
forum: General Help
---

### Post by drumanart on 2008-04-25
****
I downloaded the lightwait desktop fluxbox to test it with my UBUNTU 7.10 Gutsy. Trying to load the program from the startscreen I always land in the GNOME desktop. The same result I get if I try to start UBUNTU in failsafe GNOME - or failsafe Terminal - mode. UBUNTU allways opens with the GNOME desktop.
Any idea thks.

---

### Post by RedSquirrel on 2008-04-25
First, go into GNOME, open a terminal (Applications -> Accessories -> Terminal) and run:

```
sudo update-menus
```That will generate the Fluxbox menu.

Now, logout of GNOME.

At the login screen, in your **Sessions** list, there should be an entry for Fluxbox. Select that, login, and you should be in Fluxbox. Once you're in Fluxbox, just right-click on the desktop to access the menu.

---

### Post by drumanart on 2008-04-25
Thanks I did what you recommended but the problem keeps staying. 
If I select fluxbox, failsafe GNOME, or failsafe Terminal from the session menu I allways come to the GNOME desktop. 
What is to do?

---

### Post by kerry_s on 2008-04-25
> **drumanart said:**
> Thanks I did what you recommended but the problem keeps staying. 
If I select fluxbox, failsafe GNOME, or failsafe Terminal from the session menu I allways come to the GNOME desktop. 
What is to do?


you say you downloaded, did you use->
**sudo apt-get install fluxbox**

---

### Post by drumanart on 2008-04-26
Yes I used **sudo apt-get install fluxbox** and to be sure I did it again with the resulting message: fluxbox is already the newest version.

---

