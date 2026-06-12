---
title: "HELP! No Sounds"
date: 2008-04-24
forum: General Help
---

### Post by buknoii on 2008-04-24
Hi there! I am using a compaq C702TU laptop and my audio device is **82801H (ICH8 Family) HD Audio Controller** i tried installing ubuntu 7.10 2x this day and in my first installation everything was going well, when i log in it generated a log in sound, with that i tried installing the wifi, dvd player, and tweaked my video display so that i can use the desktop effects, then when i finished installing my dvd player i tried watching a dvd movie, the display is GREAT but there is no sound. I tried loggin in as root but still the same problem. So what I did is i re-install ubuntu, and after installing it, still the same problem... NO SOUND.

Anyone in here got an idea how to fix this? i think i just muted something here.. im a newbie in linux and any help would be deeply appreciated.

---

### Post by corstar on 2008-04-24
I would suggest right clicking on the speaker icon in the bar (usually top right) and see if it's muted, if so it's an easy fix, just unclick it.
Another thing to try is go to the command line and type "alsamixer". What you can do here is mute or change the volume on any input/output with m and up down arrows.

Failing that, check the output of these commands.. "lspci" will tell you what is hardware is loaded into your system. See if there is a sound related name here.
Then type "lsmod" this will show you what name the hardware is using.

If it shows up in lsmod or lspci, you know you don't have a hardware issue just software.

Maybe some other users can explain this better if I'm not making any sense.

---

### Post by buknoii on 2008-04-25
its already working but its weird and i cant explain it.

what i did is after my 2nd installation with ubuntu and still same problem, i installed fedora 8, after installing it, i noticed that it has sounds, i tried playing music on it and after a few minutes of testing it, i re-install my ubuntu for the third time... and VOILA! its now working hehehe

if anyone here can give me an explanation, it would be very helpful.

do you think i mess up with my irq ports?

---

### Post by corstar on 2008-04-26
> **buknoii said:**
> 
do you think i mess up with my irq ports?

I doubt it. I've installed and removed many a distro and never had hardware issues.

---

### Post by Naatan on 2008-04-26
Why don't you try Ubuntu 8.04 instead?

---

