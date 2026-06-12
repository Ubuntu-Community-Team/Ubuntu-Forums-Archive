---
title: "Some questions about X"
date: 2006-12-05
forum: General Help
---

### Post by kd7swh on 2006-12-05
I have some quick questions about the X server in ubuntu.

1. How do I boot edgy without starting X automatically?
(I would like to use the "startx" command to start X)

2. Can I start more than one x-session at a time? 
(ex. One on tty1, and one on tty2)

---

### Post by PrinceArithon on 2006-12-05
I don't know about starting more than one session, but I can tell you how to start up in command line.  I did this with my computer too, because when I first started learning Linux in 2002, it was the only way I Was allowed to set up the computer in class lol.

Anyway here is the way to do it in Ubuntu.  Plug this into your terminal.

echo "false" | sudo tee /etc/X11/default-display-manager


If for some odd reason you find a problem somewhere with this and you get back into the GUI.  Here is how to go back to default.

echo "/usr/bin/gdm" | sudo tee /etc/X11/default-display-manager


Now just incase you are using kubuntu or xubuntu make sure that you replace the gdm with kdm or xdm...that's if you are going to set your computer back to booting in the gui instead of the bash

---

