---
title: "userswitch/logout/tty lead to blackscreen"
date: 2013-08-11
forum: General Help
---

### Post by sotiris2 on 2013-08-11
I have the following problem on my 13.04 install (new on formated / partition , kept my home partition from 10.04). I can't switch between users or switch to a tty. More specifically if i select another user from the 'cog' menu the screen shows the enter password for the new user for about half a second and then goes black. Trying to type the password blindly and pressing enter yields no result. From there my only choice is to Ctrl+Alt+F1 to tty1 which shows for half a second again and then goes black. Switching back to tty7 will get me a pass box for the original running user which works normally an I can continue normal operation of PC with no problem. The same will happen if I try to logout. Blackscreen =>tty1 (blackscreen) => tty7 password prompt for running user. Repeating the process a few times (either user switch or logout) will get me to the login screen after returning to tty7 which i can then use normally and log as any user, or even get me normal switch user behavior. Rarely i get an error report for unity-greeter which i think is a process handling login (nothing specific though just telling me to submit online to canonical) 

 So to summarize my problems are:
  1) Can't switch user properly
  2) Can't logout properly
  3) Cant use tty1,2,3 etc...

System is Ubuntu 13.04 64bit on a clean root (/) filesystem using my old HOME partition from 10.04. Kernel 3.8.0-27-generic. Fully updated.
Nvidia Geforce GT620 running nvidia-310 tested. Also have tried nvidia 313 from updates.Haven't tested Nouveau but performance was pretty bad so it's not an option for more than testing.

---

### Post by sotiris2 on 2013-08-13
*bump*

---

