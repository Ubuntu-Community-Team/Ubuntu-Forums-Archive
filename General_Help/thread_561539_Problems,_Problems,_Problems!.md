---
title: "Problems, Problems, Problems!"
date: 2007-09-27
forum: General Help
---

### Post by 127.0.0.1 on 2007-09-27
well i installed beryl the day i got ubuntu. and well, now that i installed kiba-dock and played around with KDE yesterday, my login screen is KDE, and beryl dosent work anymore, and kiba-dock have a big black bar on my desktop. I am new to Linux, and ubutnu is the first distro i ever had, and i am still learning, witch is why i posted here. so to sum it all up:

-KDE is skining my login screen and i dont want it to. i want gnome to.

-Beryl crashes the moment i launch it.

-Kiba-dock creates a large black bar, witch from what i hear is a common problem. 

GOD PLEASE HELP ME!

oh, one more thing, if you don't mind me asking, what is a good theme manager? because emerald dosen't have crap for themes. thank you :)

---

### Post by cmnorton on 2007-09-27
I would tackle these problems one at a time.

1) I have seen references to a command called switchdesk. It has to be launched from a terminal window. It gives you the option to change your desktop, and apparantly offers a choice of KDE, GNOME, or TWM. I've never tried it.

2) Look in your /var/log/messages and other log files to see if Beryl left you any messages about why it crashed.

---

### Post by rzrgenesys187 on 2007-09-27
In response to the black bar problem, i had the same thing trying to install avant window manager and appparently this is the problem with that

Q: There's a big ugly black bar around AWN! How do I get rid of it?
A: You need to be running a compositor like Beryl or Compiz. xcompmgr or xfwm4 may also work, although there are known bugs with each.

found this here [http://ubuntuforums.org/showthread.php?t=385981&highlight=avant+window+manager](http://ubuntuforums.org/showthread.php?t=385981&highlight=avant+window+manager)

I imagine its the same since they are both similar docks.  Hope this leads you along.  I decided i didnt want to try to get compiz or beryl since everytime ive tried i mess something up.

---

### Post by atlfalcons866 on 2007-09-27
do you have direct rendering on? 

do 

glxinfo | grep rendering

to see if it is on

---

### Post by conehead77 on 2007-09-27
change the login screen:

just start the menu, then system --> administration --> login screen

click the tab "local" and you can change between different login themes. (all commands translated from german :) )

---

### Post by 127.0.0.1 on 2007-09-28
> **conehead77 said:**
> change the login screen:

just start the menu, then system --> administration --> login screen

click the tab "local" and you can change between different login themes. (all commands translated from german :) )

First of all, thank you all for trying to help me, ill have to do these things when i get home. (i am in school atm)

and when i try to change the login screen, i get an error message that tells me GDM is not running. how to i start it, and stop KDE?

---

### Post by HermanAB on 2007-09-28
Some general notes:
1. If you have more than 2 hardware driver problems, then you should try a different distribution, for example Mandriva, Fedora or Suse.  Each distro has its own install wizards and nobody has all equipment ever produced on the planet in their labs, so shop around and you may get lucky.
2. If you are experimenting and the whole desktop screws up, try to create a new user account, that should fix it.  If it doesn't, re-install the system, since that is the fastest way to fix it.  If you haven't created a separate /home partition, now you know why you should.

Cheers,

Herman

---

### Post by 127.0.0.1 on 2007-09-28
Sweet, thanks guys, i made a new account and now it works! :guitar: only KDE is still skining my login window, and i dont know how to start GDM.

EDIT: wtf? now i am having system crashes out of no were! thats a big problem......

---

