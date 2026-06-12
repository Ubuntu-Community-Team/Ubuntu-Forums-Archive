---
title: "Nvidia Driver wont work in Hardy"
date: 2008-04-22
forum: General Help
---

### Post by smmalis on 2008-04-22
I have tried everything I can think of, but the nvidia driver just wont work.  I have tried:
1.  Installing through the restricted control panel
2.  Installing through the NVidia installer
3.  Installing through EnvyNG
They all end up with me going into recovery mode and fixing X.  Any ideas on why this wont work?

---

### Post by nacho32 on 2008-04-22
I got mine to work it was a 7300gs justed used the Envgy thing program . dose the xconfig server show the setting?
but then I screwed up my permission under start up manager and lost it.
then gave up and went back to 710 lol

---

### Post by Zorael on 2008-04-22
Hmm.

X writes a log file upon starting it up; **/var/log/Xorg.0.log**. However, if you pick 'fix X' or safe mode, it'll get overwritten when the dumbed-down X starts, and we want to take a look at the log when it didn't work.

What you want to do is to make it break (with EnvyNG, restricted drivers, editing /etc/X11/xorg.conf manually, anything), then try to start it up, then pick safe mode or fix X, then pasting the contents of **/var/log/Xorg.0.log_.old_**. That would be the previous log file; the one where it couldn't start and instead spawned the menu where you chose fix/safe.


If you're familiar with the command line interface, you could instead pick 'exit to shell' (or whatever it says at that bulletproof X menu), then enter the following.
```
$ cp /var/log/Xorg.0.log /tmp/Xorg.0.log
$ startx
```
You'll get to the menu again, so just pick fix or safe. The copy of the log will be in the **/tmp** directory, so just open it with Gedit and paste the contents here.

---

### Post by smmalis on 2008-04-22
Alright here it is.  I installed the driver through the control panel and rebooted into recovery mode.  I went into the root console, erased all previous X logs, and ran startx.  It failed (of course) and produced the log file attached.  I had to compress it because it was too big for this forum.

---

