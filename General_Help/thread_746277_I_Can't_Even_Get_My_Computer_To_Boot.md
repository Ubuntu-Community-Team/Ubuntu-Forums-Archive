---
title: "I Can't Even Get My Computer To Boot"
date: 2008-04-05
forum: General Help
---

### Post by adn258 on 2008-04-05
Okay last night I installed mplayer and it installed.  Then I would try to open things and they wouldn't open like files or ANYTHING.  SO I restarted my computer and now I get this error that says

Kinit: name_to_dev_t(/dev/disk/by-uuid/41e55f80-e956-47de-ab1a-73bcc6c4d193) = s
da5(8, 5)

Kinet: trying to resume from /dev/disk/bu-uuid/41e55f80-e956-47de-ab1a-73bcc6c4d193


Kinit: No resume image, doing normal boot...

Ubuntu 7.10 bomb tty1


bomb login:

AND THEN all I can do is loging from the above and I get command like access but that is it Ic an't go any further I have tried everything incliuding rebooting over and over  Any help would be amazing :/?

---

### Post by cmnorton on 2008-04-05
From the login screen, can you get to a text login by pressing CTRL+ALT+F1? At least then you could get in and look at your logs and possibly uninstall mplayer.

---

### Post by adn258 on 2008-04-05
> **cmnorton said:**
> From the login screen, can you get to a text login by pressing CTRL+ALT+F1? At least then you could get in and look at your logs and possibly uninstall mplayer.

alright I will try to do that man this sucks and I have backup on my computer with sbackup but I need to have GUI access what should I do?  I the mean time I will try your idea

---

### Post by adn258 on 2008-04-05
> **adn258 said:**
> alright I will try to do that man this sucks and I have backup on my computer with sbackup but I need to have GUI access what should I do?  I the mean time I will try your idea

Okay I just tried that and I don't get anything ummmm :/ anything I can do?

---

### Post by cmnorton on 2008-04-06
> **adn258 said:**
> alright I will try to do that man this sucks and I have backup on my computer with sbackup but I need to have GUI access what should I do?  I the mean time I will try your idea

When you pressed CTRL+ALT+F1, did you get a text-mode login prompt?

Were you able to re-configure your X server?

The whole point of asking you to try CTRL+ALT+F1 was to get you logged into your PC to see if you could recover it.

---

### Post by Garamis on 2008-04-07
I am having the same problem as adn258, but I can't log in at all. It gives me the folling errors when I attempt to enter my log in name

/bin/login: error while loading shared libraries: libm.so.6: cannot dynamically load executable
init: tty1 main process ( 4148 ) terminated with status 127
init: tty1 main process ended, respawning

Ubuntu 7.10 bomb tty1

bomb login:

---

### Post by danwood76 on 2008-04-07
Your already in tty1. (ctrl+alt+F1)
try ctrl+alt+F7 that will throw you into a graphical user mode.

---

### Post by adn258 on 2008-04-07
> **danwood76 said:**
> Your already in tty1. (ctrl+alt+F1)
try ctrl+alt+F7 that will throw you into a graphical user mode.

While I thank you both I just had to replace some files and boot from the disk it worked then.  After that I got mad enough and totally erased everything and used ubuntu 8.04.  I really like it and ACTUALLY seems to have way less problems even though it is the beta version.

---

### Post by Garamis on 2008-04-08
Switching to Graphical mode doesn't work for me.  Also what files did you replace adn?

---

### Post by matey3 on 2008-04-08
I think you are already on F1, try F2 or F3. you should have 6 tty's like up to F6.
I thought you said you DO get the command prompt? can you just type gdm and go from there?

also can you hit the escape at the bootup to get a menu?
sorry i am a new bee to ubuntu but these things I had to do before and I got my server up and running..finally..
 if u get a grub menu then you can choose different kernels to boot from. 
sometimes you can also keep doing cntrl c to break the start up process and keep it from going to the problem area.
but if the different versions have different startup files then someone else with more experience with your version has to reply.

good luck.

---

### Post by fsmithred on 2008-04-08
ctrl-alt-F7 will only work if gdm is running. If you're logged in on tty1, try:

sudo /etc/init.d/gdm restart

And if that doesn't work, try:

sudo dpkg-reconfigure xserver-xorg

then try restarting gdm again.

If that doesn't work, say yes when it asks if you want to see the log, and look for the lines that begin with EE to find the problem.

---

### Post by Garamis on 2008-04-08
Part of the problem is, I can't even log in. Gives me the error msgs I posted earlier in the thread.

---

### Post by fsmithred on 2008-04-08
This sounds like a problem I had when I first installed Gutsy. Take a look at these and see if they help.

My old thread -
[http://ubuntuforums.org/showthread.php?t=577457](http://ubuntuforums.org/showthread.php?t=577457)

Bug report -
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910)

---

### Post by adn258 on 2008-04-09
> **fsmithred said:**
> ctrl-alt-F7 will only work if gdm is running. If you're logged in on tty1, try:

sudo /etc/init.d/gdm restart

And if that doesn't work, try:

sudo dpkg-reconfigure xserver-xorg

then try restarting gdm again.

If that doesn't work, say yes when it asks if you want to see the log, and look for the lines that begin with EE to find the problem.

Thanks this helped :]

---

