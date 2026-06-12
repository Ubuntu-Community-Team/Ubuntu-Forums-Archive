---
title: "nvidia enable problem on 7.10"
date: 2007-10-20
forum: General Help
---

### Post by Remataklan on 2007-10-20
I installed ubuntu 7.10 x64 on my laptop. Everything seems to work fine except i cant enable nvidia and broadcom 43xx drivers

When i try to enable them via System>Admisnistration>Restricted drivers It simply says the software source for nvidia-glx-new is not enabled. Same for the bcm 43xx.

Does anyone have any idea why?

---

### Post by mishaco on 2007-10-20
can you go to system > administration > restricted drivers manager and enable them ? they dont always default to enabled , as far as i know .

---

### Post by Remataklan on 2007-10-22
Yes i tried that. The problem is when i click enable. Ubuntu cannot enabel them.

---

### Post by UK-Wobbie on 2007-10-22
> **Remataklan said:**
> Yes i tried that. The problem is when i click enable. Ubuntu cannot enabel them.

What nvidia driver have you got? Have you got "nvidia-glx" Or the new one "nvidia-glx-new"
The best one is the new one i say it as not crashed my pc on start up any more..

See have you got any driver instilled by going to "Synaptic Package Manager"
And putting in "nvidia-glx-new" You may not have it instilled.


Or you can put this in to your Terminal!
(sudo apt-get install nvidia-glx-new)

Then when that is done log out and hit "Ctrl - Alt - And your delete back key.

That will reboot the X sever... Then log in and have a go going to 
system > administration > restricted drivers manage.... Then clicking on the show up drive!



May i ask what make is your nvidia card? You may go on some sites what will help you out.
[http://ubuntuforums.org/showthread.php?t=312333](http://ubuntuforums.org/showthread.php?t=312333)

I hope that will help you. :)

---

### Post by pfred on 2007-10-22
I had the same problem and it was because the restricted software sources weren't activated. Solution as follows:

Go to System>Administration>Software sources
Enable universe restricted and multiverse by ticking the boxes.
Click close and they will reload.
Now go to Synaptic and indeed search for nvidia-glx-new like wobbie said.
Install it and then go to System>Administration>Restricted Drivers Manager.
Now you should be able to tick the box to activate the drivers.

Done.

---

### Post by Remataklan on 2007-10-22
Hmm

I installed the 32 bit version after thi post and didnt have any problems. Both the nvidia and broadcom drivers work as they should. 

Although i didnt have time to try pfred solution. I'll will reinstall the 64bit verison and try that as soon as i have the time.

Note: In 32 bit edtion's System>Administration>Software sources restricted drivers are enabled by default. Dunno if its the same for 64 bit

---

