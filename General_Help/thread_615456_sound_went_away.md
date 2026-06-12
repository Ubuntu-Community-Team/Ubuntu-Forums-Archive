---
title: "sound went away"
date: 2007-11-17
forum: General Help
---

### Post by cywfong on 2007-11-17
Ok i have been using Ubuntu for a while now. I watching a movie on my computer, and then all of a sudden the sound went away. Everything else seems to be working except there is no sound. This happend on my other computer as well, so i rebooted the computer to 7.10 and it works now. but on this computer it seems i am having the same problem. any help without rebooting the system? thank you.

---

### Post by cywfong on 2007-11-17
bump

---

### Post by Alexis Phoenix on 2007-11-17
Some things I can think of
First guess is a hardware fault - for it to just go off like that.
Second guess - try doing ps ax in a terminal and look for alsa or esd (on mine ps ax |grep esd brings up a few things) - this tells you the sound server is running (or some other sound server, eg artsd).  You could try stopping and restarting it once you have identified what you are using. do /etc/init.d/<whatever> restart (as root)
Try lsmod and see if the module for your sound card is listed.  Try removing it with rmmod and reloading it with modprobe (both as root) - you may get information that informs you about the problem.

hth, Alexis

---

