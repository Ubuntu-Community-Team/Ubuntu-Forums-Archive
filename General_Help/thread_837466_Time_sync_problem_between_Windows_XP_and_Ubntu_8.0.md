---
title: "Time sync problem between Windows XP and Ubntu 8.04"
date: 2008-06-22
forum: General Help
---

### Post by goodbadwolf on 2008-06-22
I have dual-booted my PC with Windows XP and Ubuntu 8.04. There is a problem with the time and date displayed in the OSes. Setting the time in one OS causes it to be displayed it wrong in the other OS. For example, after setting the time to 10:45 pm on June 22 in Ubuntu , XP shows it as June 23 5 : 19 am. I use Gnome as my display manager.

Please help.

---

### Post by NilsE on 2008-06-22
Windows is using local time and Ubuntu is using GMT time or something like that so here is how to make them both use local time

In a terminal:

gksudo gedit /etc/default/rcS

Look for  this line:  UTC=yes

Change it to: UTC=no

And save it:Then set the time if it is wrong in the System/Administration/Time and Date 

Then either reboot or do this: 

sudo /etc/init.d/hwclock.sh restart

---

### Post by goodbadwolf on 2008-06-22
:). Thank you. It works fine now

---

