---
title: "Screen lock closing apps"
date: 2014-09-29
forum: General Help
---

### Post by Alisson_Lacerda on 2014-09-29
Hello,

it's my first time at the forum, so apologize me if I disespect some rule. I looked for some thread with the main rules for posting, but I didn't found :/

**My problem:**
I'm using lubuntu 14.04 and, in normal usage, with some apps open (chrome, eclipse, etc.) when I stop using the computer for certain time, the screen will turn off for "power saving" even when it's plugged. And when I move the mouse or touch some key, It comes back at lockscreen, so I type the password and lubuntu logs in with ALL THE APPS CLOSED.  
[B]
What i've tried:
[/B]Changing the settings of the power manager to not turn off the screen. 

I'm looking on every forum, and it seems like not too many people had this problem. Ok, I could do a fresh install, but I've installed too many complicated packages of software for my research project at college and it will be such a pain to make everything work again :(

I would appreciate very much if someone could help me. If, for some reason, I need to leave the notebook running for a period of time and do not touch it, I will loose all my work.

Thanks in advance!

---

### Post by linux_dream on 2014-09-29
I tried many things to remove the auto-locking. In the end what worked for me was to remove the program/package light-locker (sudo apt-get remove light-locker).
Now my screen turns black after 10 minutes of inactivity but then moving the mouse will go back to the desktop without the annoying light-locker asking for the password.

---

### Post by Alisson_Lacerda on 2014-09-29
I hope I made the **problem** clear. If not, here it goes the **step by step**:

**Using the computer > AFK for about 20 to 30 minutes > screen turns off > comes back at lockscreen > I type the password > logs in with all apps closed**

---

### Post by Alisson_Lacerda on 2014-09-29
Hey linux_dream I didn't see your post. Thanks, I'll try that and post a reply here :)

---

### Post by Alisson_Lacerda on 2014-09-29
I uninstalled it successfully, but It didn't worked out. I made a reboot and now i'm waiting for the screen to turn off again...

---

### Post by Alisson_Lacerda on 2014-09-29
Wowww!! It worked :D Thank you linux_dream. The screen turned off, but after turning on, all the apps remained open!

Thank you, again!

---

### Post by Alisson_Lacerda on 2014-09-29
Yey :D It worked! All the apps remained open after the screen turns back on!

Thank you, linux dream!!

---

### Post by Alisson_Lacerda on 2014-09-29
Yey :D It worked! All the apps remained open after the screen turns back on!

Thank you, linux dream!!

---

### Post by Alisson_Lacerda on 2014-09-29
Yey :D It worked! All the apps remained open after the screen turns back on!

Thank you, linux dream!!

---

### Post by Alisson_Lacerda on 2014-09-29
Sorry for the repeated reply.

---

### Post by linux_dream on 2014-09-29
Glad it worked :)

---

### Post by Bowgart99 on 2015-07-12
> **linux_dream said:**
> I tried many things to remove the auto-locking. In the end what worked for me was to remove the program/package light-locker (sudo apt-get remove light-locker).
Now my screen turns black after 10 minutes of inactivity but then moving the mouse will go back to the desktop without the annoying light-locker asking for the password.

I have tried this method but unfortunately the application are still being closed when the lock screen is  invoked.  Any other idea's, I am running UBUNTU 14.04.

---

