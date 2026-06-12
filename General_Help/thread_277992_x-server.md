---
title: "x-server"
date: 2006-10-15
forum: General Help
---

### Post by serious7 on 2006-10-15
hi, recently i was trying to get xgl to run on ubuntu and to my surprise it actually worked. I have 128 ram. nvidia geforce 2 mx-400 (64 mb) and 1.5 ghz. Now, the problem with xgl was that it doesn't load on startup so i had to manually enable it. Otherwize it worked great. But then i tried to fix the startup problems and it just doesn't load itself on startup. So i decided to install beryl from the guide here. Installation was successfull and i rebooted and found myself stuck in the command line with the x-server error. I had fixed this before using sudo dpkg-reconfigure xserver-xorg but it doesn't help me now. Like, it loads the nvidia splash screen, then goes to command line, loads splash screen again, goes back to command line and does that for 3-4 times before it stays in command line and gives me the x-server message. ](*,)

---

### Post by serious7 on 2006-10-15
oh, i use dapper

---

### Post by serious7 on 2006-10-15
bump

---

### Post by Dr. Nick on 2006-10-15
from command line try

sudo nano /etc/X11/xorg.conf

change the nvidia line to "nv" and that will bypass the drivers, this may get you into a gui, without beryl. How did you add it to the startup? If its a bug in beryl then try using the command line to update it

sudo apt-get update
sudo apt-get dist-upgrade 

to get all the newest version of the system.

---

### Post by serious7 on 2006-10-15
ok i fixed all that, ubuntu is running but now it's a different problem related to x-server. I'm trying to get xgl to work but it doesn't want the xorg file to be edited. It works when i run it manually but i want it to load on start up. Everytime i edit the xorg. file, the thing crashes. Now it got to the point where i can't even install compiz from synaptic (i deleted it to fix the problem). Some error about broken dependency with compiz-plugins. Any way out?

---

### Post by Dr. Nick on 2006-10-15
compiz is not being used as much now. I would look into beryl which is a for of compiz. Their are guides for dapper out thier, I have only used it on edgy though.

How are you adding these to startup? I have always used the system-prefrences-sessions menu in gnome to do it.

---

### Post by Dr. Nick on 2006-10-15
here is a dapper guide you can try
[http://ubuntuforums.org/showthread.php?t=268036](http://ubuntuforums.org/showthread.php?t=268036)

before doing that I would remove all xgl+compiz stuff you can find, Including anything you did to try and get it to run on startup and get back to a default xorg. Then follow the guide

---

