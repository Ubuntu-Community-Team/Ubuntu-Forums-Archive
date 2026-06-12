---
title: "Asus laptop freezing hard, caps lock light flashing"
date: 2016-01-05
forum: General Help
---

### Post by Antoni_T. on 2016-01-05
Hello guys,  

Recently my laptop started freezing whitout warning.(after my girlfriend used it..lol)Joke aside,I reinstalled Ubuntu to make sure it is not wierd experimental software I downloaded that is causing the problem. During the first install it froze up before the end of the setup. Something telling me that it  maybe a harware problem. The symptom, I could see is the caps lock light flashing at a regular interval. This computer has been hard stop several times.I had an old HHD on this computer and I tought maybe this was it going bad, so i replaced it with a new Kingston SSD. Still freezes solid, like a liquid nitrogen dipped banana.
  
The model of the computer is a G53sx.

I know the computer is old, made 2011-07 :3 but it is a great machine that rocks with Ubuntu!

Any input or advices on what I should  look at / do to maybe save the beast ?

Cheers!

---

### Post by ajgreeny on 2016-01-05
Hi Antoni_T and welcome to the forums.

BACKUP, BACKUP, BACKUP!
You could possibly have a hardware problem, so this is the #1 instruction before trying the actions below.

A flashing cap-lock light is usually a sign of a kernel panic, which in your case, and thinking about your comment > This computer has been hard stop several times. could be caused by a filesystem corruption.

You can run a filesystem check.  If you can get the machine to start and allow you to login use command ```
sudo touch /forcefsck
``` and then reboot.  That may be sufficient to repair any problems, but if not you may need to boot to a live Ubuntu system and run the command ```
sudo e2fsck -vy /dev/sdx#
``` where sdx# is your root partition.

Try this and report back how you get on, but don't forget my first advice, ie BACKUP!

---

### Post by Antoni_T. on 2016-01-05
Hey thanks for your quick answer, it is really appreciated!

No backup is necessary since it is a new drive.

Okay I did run the command: [COLOR=#000000][FONT=Ubuntu Mono]sudo touch /forcefsck. No information about the process in the Terminal.
 
Is it supposed to give some feedback on what it found to be working or not working wih the partition?

thanks,

[/FONT][/COLOR]

---

### Post by Antoni_T. on 2016-01-05
Now it does not freeze anymore. Atleast for the moment. However, Ubuntu experiences internal error titled ''NMI watchdog:BUG:soft lockup -cpu#0 stuck for 23s![fuser:3152]

the "System program problem detected" keep popping up.

If it´s the processor cores not responding maybe the I7 chip is fryed?

(Edit: it does freeze again)

---

### Post by ajgreeny on 2016-01-05
The command ```
sudo touch /forcefsck
``` forces the system to run a filesystem check (fsck) at the next boot but otherwise does not do anything itself, so if you did not reboot no check will have been carried out.

If you are still having problems it may still be worth running the second command I showed from a live system ```
sudo e2fsck -vy /dev/sdx#
``` where sdx#is your root partition, probably sda1 if Ubuntu is the only OS you have on the machine, though it might be something else.  Run command ```
mount
``` from the running installed OS to find out what is the / (root) partition.

---

