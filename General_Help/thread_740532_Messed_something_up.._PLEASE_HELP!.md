---
title: "Messed something up.. PLEASE HELP!"
date: 2008-03-30
forum: General Help
---

### Post by jhyland87 on 2008-03-30
ok, so here is the story, I was trying to install apache2 and php5 on my ubuntu 7.10 desktop, and I did the install just right, however I tried to make an index.php file in the www folder, it said I didnt have permissions. So I went to the users and groups administration, and I added my account (administrator) to the root group, and made the administration home folder the same as the root home folder..

I restarted my computer, now when I go to login as administrator with the right password, I get this error..

> Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean  that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

I can go into safe mode and login as root, but what are the commands to reset the users and groups back to default

I have made some progress but still not able to login

When i login as root in the safe mode, and run startx, it tries to log me in as root in the gui interface, and says it cant enable switch user, and I try to go to system>administration>users and groups... but I cant, the entire administration menu is out of reach, I dont have access.. even though im root

---

### Post by jhyland87 on 2008-03-30
Anyone able to give me a hand?

---

### Post by jhyland87 on 2008-03-30
22 views and not a single reply?

---

### Post by tempest on 2008-03-30
Give this a try. I found it in another thread somewhere and I think this worked for me once or twice in the past.

Login in on one of the failsafe sessions and delete .ICEauthority from
your home folder. 

To be safe you might want to just rename it to something like .ICEauthority_old

---

### Post by jhyland87 on 2008-03-30
> **tempest said:**
> Give this a try. I found it in another thread somewhere and I think this worked for me once or twice in the past.

Login in on one of the failsafe sessions and delete .ICEauthority from
your home folder. 

To be safe you might want to just rename it to something like .ICEauthority_old

ok well the only account I have access to is root, which I have to login via the safe mode terminal.. I dont believe thats a failsafe account

---

### Post by jhyland87 on 2008-03-30
when I login to root in safe mode terminal, and type startx to get into the gui interface, I get in it, but I have no access to anything at all.... only in the terminal

---

### Post by jhyland87 on 2008-03-30
im so pissed right now, screw it, ill just reload ubuntu

---

### Post by darkorical on 2008-03-31
I was trying to install apache2 and php5 on my ubuntu 7.10 desktop and now I'm having the same basic issue except it wont let me log in it keeps telling me that my password is wrong I can log in via a fail safe and get the gui to load tho but I cant find the file you said to delete.

I was following the directions from this page [http://www.softwareforeducation.com/lamp/conf/index.php](http://www.softwareforeducation.com/lamp/conf/index.php)

---

