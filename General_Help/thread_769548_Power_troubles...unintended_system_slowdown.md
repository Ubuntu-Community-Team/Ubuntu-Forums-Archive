---
title: "Power troubles...unintended system slowdown?"
date: 2008-04-26
forum: General Help
---

### Post by eaglestrike7339 on 2008-04-26
Ok, so here we go. I am running ubuntu 7.10 (upgraded for 7.04 once it came out). It is the desktop version, but I am using it as a server to serve a few internal webpages, torrentflux (read LAMP server), Samba shares, webmin and SSH 

It is an old emachine w/ a Celeron D, 1.5gigs of ram, and a 160g harddrive. 

Problem is, is that every so often, (though I have turned all power management in the GUI turned off), blacks out the screen and goes to "sleep", which it is very hard to rouse it from. If I don't restart it, it experiences MASSIVE slowdown. Think: mouselag. Bad. 

How would I solve this problem? Pretty soon, I am going to get a new system and install 8.04 on it, but is there another solution that would prevent the system from sleeping?

Thanks to all, 
M@

---

### Post by sdennie on 2008-04-26
What exactly do you mean by "sleeping"?  Does the machine have a monitor hooked up to it and does the monitor go into power savings mode?  Also, when it begins to react slowly, is it possible to log into the machine and run "top" to see if anything is killing the CPU (or, more likely, the disk)?  Last, can you bringup gconf-editor on the server and look in /apps/gnome-power-manager to see if there are any options that are unintentionally checked?

---

### Post by eaglestrike7339 on 2008-04-27
well, first the screen dims and goes black, then the monitor drops the signal and goes to sleep. On resume, the monitor wakes up and I can see the mouse, but no prompt comes up to log back in for a long time (~5minutes)

I changed some options on power management, and we will see if it happens again. Running top tells me that Xorg is almost always taking the most CPU power, but i´m not sure how to tell how much disk space is being used. 

Thanks alot, and hopefully this will work, 
m@

---

