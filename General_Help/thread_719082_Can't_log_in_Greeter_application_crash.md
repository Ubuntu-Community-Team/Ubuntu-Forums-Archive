---
title: "Can't log in: Greeter application crash"
date: 2008-03-08
forum: General Help
---

### Post by AvengingAngel718 on 2008-03-08
Everytime i boot up, after the ubuntu loading screen and before it would bring up my login screen, i get an error saying the greeter application has crashed and i cant log on or do anything. I installed a new login theme last night and i believe it to be the cause of the error. Is there a way to restore my login defaults through the terminal on the live cd, because that is the only way i can currently run ubuntu. If not, are there any other possible solutions besides reinstalling? i just reinstalled 2 days ago after really messing things up and just got things set up before having this problem, so i'd rather not waste 2 more days.

---

### Post by midlifecrisis on 2008-03-10
I've got this error after trying to update from 7.04 to 7.10.

I've read the post about accessible login setting in the login screen, but I can't find the login manager in Xfce.

when I "startx" I get errer about the HAL and the greeter error flashes up every few minutes.

Is there a way to role back my install?

---

### Post by kapello on 2008-03-10
From the command line you can try 

sudo gdmsetup

---

### Post by midlifecrisis on 2008-03-10
editng the 2 files in this post sorted it out for me: [http://ubuntuforums.org/showthread.php?t=190310&highlight=greeter+application+crash&page=2](http://ubuntuforums.org/showthread.php?t=190310&highlight=greeter+application+crash&page=2)

---

### Post by Kain000 on 2008-07-06
Hey everyone,
Im currently experencing the same problem, installed a new logon theme and this morning my laptop is in an endless cycle of logon reboots.  
How to I get the text file open to edit it via the command line.

or is there some sort of recovery mode where I can be inside the GNOME system and just change the logon theme inside the GUI? 

I've tried to open the file to edit it with gedit and no luck so for now I'm pretty much up the river.

-sucks Because I was up until 5 am and had FINALLY after like a week of tinkering worked out the kinks in my home NFS server and thismorning.....
ahhhhhh!
thanks
-sean

---

