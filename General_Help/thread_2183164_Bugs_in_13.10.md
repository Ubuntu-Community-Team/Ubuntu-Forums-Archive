---
title: "Bugs in 13.10"
date: 2013-10-23
forum: General Help
---

### Post by mabtifro2 on 2013-10-23
i first upgraded to 13.10 beta like a month ago and there were a ton of bugs. many have been fixed since the final release came out a few days ago, but some remain. these are the three most annoying:

1. when i close the lid to my laptop (acer v5-171) and reopen it and type my password to unlock the screen, the command prompt is open. like when you hit the alt key and that command prompt comes up, thats what it does. but only after closing and opening the lid. it doesn happen if i lock the screen manually and unlock it.

2. my keyboard doesnt work with tor browser. i have to type addresses inside a word doc then copy and past them into the address bar of the browser to get it to get to an adress.

3. rhythmox is kinda jenky now. the shortcuts dont work anymore (for example ctrl-space to pause a song) , and it almost always freezes when i first start it and try to play a song. i have to force quit, then reopen it.

i hope someone has the solution to these problems. thanks

---

### Post by mc4man on 2013-10-23
1. known bug, will be fixed in an SRU update at some point. If really bothered then install gnome-settings-daemon package from ppa in comment 32
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1227920](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1227920)
2. no idea, don't use
3. don't really use RB but pause is ctrl+p

---

### Post by mabtifro2 on 2013-10-28
thanks for your reply.

these are some other annoying bugs, if anyone has solutions, please share:

4. when i start the computer and it get to the desktop, i get a "system program problem detected" pop up box. actually i get three.

5. there is tons of script on start up, like way more than 13.04

6. i cant change the time! this one just started happening today. the time is wrong, it's set at "UTC" time zone, and i cant change it. i can choose any city i want, or choose to set it manually, but it doesnt save. there is no "ok" or save button, so i have to "x" out of the box and nothing changes.

---

### Post by Dennis N on 2013-10-28
#4 is probably from apport if the notice asks to send a report. It is a feature, not a bug; it's purpose is to report a problem to headquarters. If desired, you can disable it from **/etc/default/apport** where you set **enabled=0**

---

### Post by mabtifro2 on 2013-10-28
thanks. btw number 6 was actually just that my clock was frozen, it wasnt moving, even after reboot. but i fixed the problem when i put the computer to sleep and woke it back up

---

### Post by mörgæs on 2013-10-28
> **mc4man said:**
> 1. known bug, will be fixed in an SRU update at some point. If really bothered then install gnome-settings-daemon package from ppa in comment 32
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1227920](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1227920)


It's fixed now by enabling proposed (which means that the fix will likely come out through the default repositories soon).

---

