---
title: "Set a script to be executed as root at system start"
date: 2015-03-25
forum: General Help
---

### Post by smarty2 on 2015-03-25
Hi !
To make most use of my worthless old laptop, I am planning to use it as a media server the whole time it is on. Problem is, it may be shut down after a while and I need it to do the following at every system start :
1. As root mount my portable hard disk to a particular directory ( eg. ~/myDrive ) 
2. Connect to my wifi and check if internet is OK. If not try again after 100 seconds.  Do it untill connected.
3. Make sure the local IP address assigned is a particular value, eg. 192.168.0.103. I dont want my router it to assign some other IP, as my other devices ( like Windows Box ) has shortcuts to /samba/192.168.0.103. 
4. Run qBitTorrent in Service Mode 
5. Start a VNC session
6. Start SAMBA services. 

I want all this done when system boots up to Ubuntu without any user intervention. If someone looks at the screen of my laptop it would only show a login screen. 

Can anyone help? I am good at scripting all the above, but dont know how to set it at start or how to do step (3).

---

### Post by kerry_s on 2015-03-25
/etc/xdg/autostart ?

---

### Post by Lars Noodén on 2015-03-25
Step #3 is usually done by your router.  It varies by brand and model but there is usually some place to associate a fixed address with the MAC address that the client claims it has. 

About where to run the script, the simple option is to run it from /etc/rc.local, which gets run after everything else is running.

---

### Post by smarty2 on 2015-03-25
Will it be run as a ROOT ? Sudo?

---

### Post by Lars Noodén on 2015-03-25
Anything launched from /etc/rc.local will run as root.  If you want to launch as another user and not root then precede the script (in rc.local) with *sudo -u smarty2* or  *su -l smarty2 -c* to launch it as smarty2

---

