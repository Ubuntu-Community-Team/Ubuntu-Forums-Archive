---
title: "Cursor freezes after startup Xubuntu 16.04"
date: 2016-09-24
forum: General Help
---

### Post by Ralph L on 2016-09-24
I installed Xubuntu 16.04 some time back.  Always after startup the cursor is frozen--won't move (I use the touchpad).  Workaround is ```
Ctrl-Alt F1
login by typing my user name (admin permission)
enter password
sudo rmmod psmouse
sudo modprobe psmouse
Ctrl-Alt F7
```  Having to do this on each start up is a nuisance.  Anybody else have this problem?  Anybody have a fix?  This works fine in Xubuntu 14.04 and has prevented me from moving to 16.04.

---

### Post by kc1di on 2016-09-25
Hi Ralph L,

Give us a little more to go on.  What is your machine make, model, ram etc. 
which mouse are you using?  have you tried the additional driver app to see if there is a better driver to install?

---

### Post by Ralph L on 2016-09-26
kc1di,
Thanks for your response.  My computer is an old Dell Latitude D610 laptop.  It has 2 G of Ram.  The OS as I said before is a new install of xubuntu 16.04.  I still have xubuntu 14.04 that I use for my daily tasks and I don't have this problem.  During installation I set "Don't need password to login" or something like that.  I use the touchpad for the mouse.  

Also, I noticed that if I do Ctrl Alt Del and get the login box, that the cursor works until I login, and then freezes again after I attempt to login.

Note that I updated the original post to show that after I do Ctrl Alt F1, I have to login and enter my password--even though I have things set to not need a password.  This hints to me that the login program may be failing.

---

### Post by Ralph L on 2016-09-27
I restarted from scratch.  I re-downloaded xubuntu 16.04.1, reinstalled it, and it fixed this and another problem.  Don't know what went wrong, but now the cursor moves after boot.  In addition, I am now logged in as I should be.  Thanks to everyone who responded.

---

### Post by kc1di on 2016-09-27
Glad you got it sorted out. :)

---

