---
title: "Computer Became Extremely Slow"
date: 2008-06-17
forum: General Help
---

### Post by DiverseNerd on 2008-06-17
Hi everyone,

I finally retired my old gaming rig and built a new one, and decided to try out Ubuntu 8.04 on the old workhorse.  The live-cd was slower than normal, but I decided that must have been because I was using a slower drive than before.  It took HOURS to install, when it used to install 7.10 in less than 1 hour.  When I restarted after install, it took it 10 minutes to boot, and was EXTREMELY slow in the OS.  When you clicked on the "Applications" menu, it took 5 seconds for it to open.  

I thought that it might be a bad burn, so I installed 8.04 on my new rig, and it was perfect.  I reinstalled Windows XP, and it was equally slow, as was OSX86, which said it would take over 5 hours for a light install.  I figured that it could have been that the hard drive I put in it was bad, so I swapped that out, and it was slow still.  

The fans seemed to be running abnormally high, so I checked the CPU temperature in BIOS, and it said it was at a whopping 245 degrees Fahrenheit!  Knowing this couldn't be right, I cleared the CMOS and tried again.  The fans were now quiet and the BIOS indicated that the CPU was idling at 45 degrees Celsius.  I haven't got a chance to run Memtest86 yet, which I will do when I get home.  

System Specs:

Compaq Presario SR1900NX
Intel Celeron D 352 @ 3.2GHz
1.5 Mb DDR 400mhz ram
GeForce 8600 gt 256mb (tried the integrated ATI Radeon Xpress 200 but that didn't work either) 
Ultra 400watt psu

Any thoughts?

---

### Post by DiverseNerd on 2008-06-17
bump

---

### Post by DiverseNerd on 2008-06-17
Alright, an update;

Ran Memtest86.  Says no errors found but the progress kept resetting each time it got to around 70%.  Memtest also reported that my processor was a Pentium D, not a Celeron D.  The bios no longer says what type of processor it is, only that it is an Intel and that it is at 3.2 ghz.  

Plz Help!

---

### Post by cariboo on 2008-06-18
You might want to check if there is a bios update.

Jim

---

### Post by DiverseNerd on 2008-06-18
> **cariboo907 said:**
> You might want to check if there is a bios update.

Jim

I have the latest update

---

### Post by DiverseNerd on 2008-06-18
> **DiverseNerd said:**
> I have the latest update

Hmm... I was messing with it today, maybe the 8.04 Install somehow corrupted the bios?

---

### Post by lisati on 2008-06-18
> **DiverseNerd said:**
> Alright, an update;

Ran Memtest86.  Says no errors found but the progress kept resetting each time it got to around 70%.  Memtest also reported that my processor was a Pentium D, not a Celeron D.  The bios no longer says what type of processor it is, only that it is an Intel and that it is at 3.2 ghz.  

Plz Help! 
Don't panic about what the BIOS says, a change in the messages sometimes happens: My laptop used to tell me that it had a Celeron M cpu, but after I updated the BIOS it just pops up the intel logo.

> **DiverseNerd said:**
> Hmm... I was messing with it today, maybe the 8.04 Install somehow corrupted the bios?

Unlikely. Does your new BIOS have a setting where you can reset it to defaults?

---

### Post by DiverseNerd on 2008-06-18
yes, I have tried setting it to defaults, i tried clearing the cmos.... my God this thing is slow :( .  Could the motherboard just be fried?  Is there some way to flash the bios back to factory version?  

Thanx for any help!

---

