---
title: "Weather for gnome-fallback session"
date: 2015-11-06
forum: General Help
---

### Post by jeffneedle on 2015-11-06
Hi.  Just installed 14.04, 64-bit.  I hate the buttons on the left side, but everything I read tells me I have to use gnome-fallback in order to get the buttons moved to the right side, where I expect to see them.  So I did that.

I miss having a weather indicator.  Is there a way to install one on the top panel?  It would be wonderful to have a complete report -- temp, humidity, forecast, etc.

Thanks for any help you can offer.

---

### Post by raja.genupula on 2015-11-06
Have you tried installing 

sudo apt-get install gnome-applets gnome-flashback gnome-panel metacity notification-daemon

Let me know if its not working for you.

---

### Post by jeffneedle on 2015-11-06
jeff@jeff-All-Series:~$ sudo apt-get install gnome-applets gnome-flashback gnome-panel metacity notification-daemon
[sudo] password for jeff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnome-flashback
jeff@jeff-All-Series:~$ 

Evidently something  missing.  Nothing in Software Center for "gnome-flashback" -- very confused.

---

### Post by Frogs Hair on 2015-11-06
Try installing the components one at a time. ```
sudo apt-get install gnome-session-flashback
``` ```
sudo apt-get install gnome-applets
``` If the packages are found and installed, logout and select the session at login from the icon top right of where you enter the password.

---

### Post by jeffneedle on 2015-11-06
Many thanks.

---

