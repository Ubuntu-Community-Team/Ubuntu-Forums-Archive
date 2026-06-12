---
title: "Ubuntu Software  Button - Not Populating 17.04"
date: 2017-09-20
forum: General Help
---

### Post by GeorgeBerz on 2017-09-20
When I click on  the software library button  or software center or app launcher...

It does not populate 

audio video games

---

### Post by Perfect Storm on 2017-09-20
Try update the system. Close software center and open the terminal:
```
sudo apt update && sudo apt upgrade
```
You may logout/login before it takes affect.

---

### Post by GeorgeBerz on 2017-09-20
This is what I get doing your recommendation.


george@george-desktop:~$ sudo apt update && sudo apt upgrade
[sudo] password for george: 
Reading package lists... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
george@george-desktop:~$

---

### Post by Perfect Storm on 2017-09-20
It means you have the software center, update application, or synaptic are running, please close them first. If you want to make sure that everything is closed logout/login would do.

---

### Post by GeorgeBerz on 2017-09-20
I have logged out and also rebooted many times as others on the web have given that advice

Mostly it hangs on opening screen, then sometimes I get some details. I am on a 100mbit line and have just done the install of 17.04 and team viewer, its a fresh install,  broken module? can you reinstall software manager?

---

### Post by GeorgeBerz on 2017-09-20
I get this after awhile it never populates...

---

### Post by Perfect Storm on 2017-09-20
Try push the update button and hit the refresh button (upper left) in ubuntu software center.

---

