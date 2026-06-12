---
title: "Login Screen Gone"
date: 2008-02-25
forum: General Help
---

### Post by Aurooo on 2008-02-25
Alright so my login screen was working great. Then I installed a spred firefox theme for it. I followed the instructions and when I selected it I logged out to test it out and I get an error about how its not working.. [http://art.gnome.org/themes/gdm_greeter/744]("http://art.gnome.org/themes/gdm_greeter/744") Heres a link to the them. I installed it by running gdmsetup and dragging it in and the preview looked like it was working. After it stopped working I booted up onto my vista partition and have done lots or research but found no anwser on fixing it. The comment says they restored GDM's config files but I don't know how.
Methods I've tryed in both terminal (Screen goes black CTRL+ALT+F2) and recovery mode.
sudo dpkg-reconfigure gdm
sudo apt-get install gdm
sudo apt-get remove gdm then sudo ap-get install gdm
Tryed sudo rm .rf .gnome .gnome2 .gconf .gconfd .metacity  It says they are there but won't let me remove them.
Thanks in advance, Auro

---

### Post by DieB on 2008-02-25
try:

sudo aptitude purge gdm 

that will uninstall and delete the config files and afterwards install it again:

sudo aptitude install gdm

did it help?

---

### Post by Aurooo on 2008-02-25
Posting from Ubuntu 7.10 Everything worked Great!!! But 2 things.. not sure where my windows partition went =( its mount point was media/sda1 not sure how to remount it and the other thing is my quick user switch applet isn't working anymore it offered me to delete it I said no. First issue kinda big 2nd issue not so much. Thanks, auro

---

### Post by Aurooo on 2008-02-26
Fixed the 1st issue by restarting windows properly and going back into ubuntu :D

---

