---
title: "suddenly lock screen freeze"
date: 2020-02-18
forum: General Help
---

### Post by mprovitina on 2020-02-18
Hello everyone,
I have 5 workstations running Ubuntu 19.10 since the last friday, and everything worked nicely until this afternoon.
Suddenly each workstation started to have the same problem: when I try to unlock it from the lock screen it seems frozen. I can move the cursor but anything responds (can't click the top-right buttons for connection, volume or power), pressing Enter it doesn't respond at all (it should be supposed to ask for user's password and come back to desktop).
The only thing that works it's Ctrl+Alt+F3 (or whatever F-key) to use tty console. I can login from there and use any command.
The only solution to access the desktop again is to reboot.

I really can't figure out what's happening, firstly because I often unlocked the workstations until today without any problem like this, it just started this afternoon. I haven't installed new softwares today, neither modified any config, system file or whatever.
For the moment I removed the automatic screen lock (it was set after 5 mins of inactivity) but I'd need it back on asap. Any ideas on what should I check? Thank you in advance

---

### Post by Frogs Hair on 2020-02-18
Support request moved to *General Help*.

---

### Post by mprovitina on 2020-02-22
up

---

### Post by mprovitina on 2020-02-27
Unfortunately I haven't found a solution too, still just keeping the lock screen disabled.

---

### Post by CelticWarrior on 2020-02-27
Happening in five at the same time strongly suggests a common cause. In this case there might have been an update that created the problem. 
I suspect something related to the graphics subsystem. 

Can you please check the latest updates, kernel and graphics driver? Also please, it goes without saying, some information regarding the hardware will certainly be useful.

---

### Post by mprovitina on 2020-02-28
Sure, thank you.
So regarding the hardware, it's exactly the same for every workstation. The motherboard is an Asus TUF GAMING X570-PLUS, with a Ryzen 9 3900X, GeForce RTX 2070 SUPER, 64Gb RAM ddr4, SSD Samsung 960 EVO 1Tb and a 4Tb HDD for storage.

During the last week we had a huge problem with all the machines, probably caused by some update, so we reinstalled Ubuntu 19.10 from scratch on each one (minimal installation) and disabled every update.
cat /proc/version returns: Linux version 5.3.0-40-generic (buildd@lcy01-amd64-026) (gcc version 9.2.1 20191008 (Ubuntu 9.2.1-9ubuntu2)) #32-Ubuntu SMP Fri Jan 31 20:24:34 UTC 2020

---

### Post by CelticWarrior on 2020-02-28
If you have a problem with a newer kernel you should be able to also boot from the one that was working. There's no need to disable updates and you shouldn't, the problem - if any - with a certain update is typically solved in the next one.

And you need drivers for the GeForce RTX 2070 SUPER that aren't included in the minimal installation. You may need to add the additional graphics drivers PPA in order to get the newest driver that those cards need. The support given by the default open-source driver to any very new card is typically insufficient and hit and miss. I'm surprised it only freezes with the screensaver.

---

