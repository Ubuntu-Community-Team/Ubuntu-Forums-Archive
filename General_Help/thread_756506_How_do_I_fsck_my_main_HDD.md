---
title: "How do I fsck my main HDD?"
date: 2008-04-15
forum: General Help
---

### Post by denzilla on 2008-04-15
My PC has frozen a few times and I've had to hold the power button till the PC shuts off. How do I run a fsck on bootup? I read somewhere on here to open the terminal and type "sudo shutdown -F" but all that returned was a "time expected" message. Running Hardy btw. Yea, I know its beta and there is nothing important on this PC. Just trying to learn a bit :p

---

### Post by sekinto on 2008-04-15
If it says "time expected" you should be able to add "now" at the end of the command to do it that instant. I'm pretty sure you could also run fsck from a Live CD.

---

### Post by niteshifter on 2008-04-15
Hi,

To force an fsck run on boot do the below in a terminal:
```
sudo touch forcefsck
```
on the root for each partition + file system you wish to check.

Example, the whole filesystem on a single partition (Ubuntu default installation):
```
cd /
sudo touch forcefsck
```
then shutdown or restart the system.

Example, two partitions. One is / the other /home, to fsck /home;
```
 cd /home
sudo touch forcefsck
```
and shutdown or restart.

---

### Post by denzilla on 2008-04-16
Thanks :)

---

