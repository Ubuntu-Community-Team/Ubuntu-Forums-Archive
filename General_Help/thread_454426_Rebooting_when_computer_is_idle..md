---
title: "Rebooting when computer is idle."
date: 2007-05-25
forum: General Help
---

### Post by xconspirisist on 2007-05-25
Hey. Having some problems with my computer rebooting when idle. Using feisty. It's as solid as a rock while using it, but if left alone for about 2 hours it seems to be rebooting (confronted with the login screen when I get back). A friend mentioned that he actually saw a full reboot though.

I don't really know where to look in logs, but a bit of grep'ing around didn't find anything exciting. I'd be most grateful if you could help me out. 

Many thanks in advance.

---

### Post by Big_Croc7 on 2007-05-25
Did your friend see it shut down as well as boot up?  Just to check it's not temporary power cuts causing it? (unlikely, but possible)

---

### Post by xconspirisist on 2007-05-25
I'm not sure, although my file server is on 24/7, so it can't really be a power cut.

---

### Post by aks44 on 2007-05-25
```
cat /var/log/Xorg.0.log | grep Time:
```will tell you the last time Xorg started.

That's the closest I can think of...

---

### Post by xconspirisist on 2007-05-26
Weird. I booted my computer up at about 10:00 this morning, left it at about 11:30, and apparently the x server started up again at 14:35. So it defiantly is doing something after about 2 hours.

---

### Post by pmg on 2007-05-26
To verify it really is rebooting and not the Xserver dieing and being restarted, look at the output of the "uptime" command and/or the "who -b" command.  They will tell you how long the kernel has been up and when it last booted, respectively.  You might also want to look at the output from the command "last -10 reboot" to see how often it's rebooting when you're away, and if it does it every two hours when left alone.

---

### Post by xconspirisist on 2007-05-30
Woah, that **last** command is really useful, I wish I had known about it sooner. 

It looks like it could well be logging me off, or the xserver crashing, etc, there arn't many reboots in there. 

Can anyone suggest a next step?

---

### Post by pmg on 2007-05-31
Glad that narrowed it down.  I assume you've checked that it's not just a screen saver kicking in.  (If it's set to lock the screen,  unlocking it does look somewhat like the login screen.  Go to "System -> Preferences -> Screensaver" to check the settings.)

I don't know much about the Xserver myself, but I'd start by looking at the log file it writes.  Either go to "System -> Administration -> System Log" and look at the Xorg.0.log, or look at the file /var/log/Xorg.0.log.  You might also want to look at the prior log, Xorg.0.log.old too.  I'm not sure what to look for in there, but maybe a problem/error will jump out at you.

---

### Post by xconspirisist on 2007-05-31
Solved it. It's a very nasty bug in gnome-screensaver, which gets a sig 15, then the xserver crashes. 

I fixed it by installing xscreensaver.

---

