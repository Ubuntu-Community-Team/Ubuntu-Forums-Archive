---
title: "how can i remove ATI drivers?"
date: 2007-04-24
forum: General Help
---

### Post by allforcarrie on 2007-04-24
I am running ATI restricted drivers, how can i go back tot he default drivers?

---

### Post by aldenhg on 2007-04-24
Open a terminal and type "sudo apt-get remove xorg-driver-fglrx"
Then, type "sudo gedit /etc/X11/xorg.conf" and search for "fglrx." replace "fglrx" with "radeon" or "ati" and save. Restart gnome by hitting Ctrl+Alt+BackSpace and you should be good to go. 

I would reccomend backing up your xorg.conf file beforehand in case something goes wrong.

---

### Post by strabes on 2007-04-24
That's kind of a small change to back up your entire file for. You can just switch to a virtual terminal with ctrl + alt + F1 and then run "sudo nano /etc/X11/xorg.conf" and change the 1 setting back. You can also reinstall fglrx in the virtual terminal.

---

