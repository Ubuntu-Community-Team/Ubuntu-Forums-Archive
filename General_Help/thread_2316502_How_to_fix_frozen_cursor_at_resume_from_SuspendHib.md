---
title: "How to fix frozen cursor at resume from Suspend/Hibernate"
date: 2016-03-08
forum: General Help
---

### Post by Ralph L on 2016-03-08
About 1 out of 20 times when I resume my xubuntu 14.04 from suspend or hibernate, the cursor is frozen.  Rather than rebooting the computer from scratch I found (from a web site I can't remember) to do the following:```
Ctrl Alt-F1 to log out of desktop
if not still logged in, login with username and password (the login command should automatically appear if you are not logged in)
sudo rmmod psmouse
sudo modprobe psmouse
Alt-F7 to return to desktop
``` I have seen some forums that say the merely Alt-F1 followed by Alt-F7 will sometimes work.

Another way I have seen documented is to bring up Terminal with Ctrl Alt-t, and type in the 2 commands above.

I am posting this merely to publicize this solution a little more so that it is available to people who are having this problem.

---

### Post by Clode_Runner on 2016-05-22
when I resume my xubuntu 16.04 from suspend or hibernate, the cursor don't appear. I can click but don't be sure when the cusor is

---

### Post by Ralph L on 2016-05-24
clode_runner

Try the two methods that I listed--one using Ctrl Alt F1, and the other bringing up a Terminal using Ctrl Alt t. Then type in the commands I gave.   If these don't work I am unable to help. 

Good Luck!!!

---

