---
title: "Kubuntu only beeps"
date: 2021-03-04
forum: General Help
---

### Post by zieborn on 2021-03-04
My Kubuntu install (on a really old system) only beeps when it starts up (black screen, three beeps repeating). For awhile it would restart after a couple tries, then it worked if I changed monitors. Now nothing. Computer is real old, and I just recently (few months ago) got the "Your PC is no longer supported" message.

---

### Post by CatKiller on 2021-03-04
> **zieborn said:**
> (black screen, three beeps repeating) 

Three beeps would generally mean memory failure, IIRC. 

>  Computer is real old, and I just recently (few months ago) got the "Your PC is no longer supported" message.

32-bit processors (so from before ~2003) are no longer supported by any Ubuntu flavour.

---

### Post by grahammechanical on 2021-03-04
Try obtaining a PDF version of the motherboard user manual from the manufacturer's web site. If you do not have a paper version. That will possibly explain what the BIOS error messages mean. These beeps are being produced by the motherboard running Power-On Startup Tests (POST). This happens every time we power-on.

How long have you had Kubuntu installed on this machine? Does the motherboard put any written error messages on the screen? This problem is happening before the BIOS looks for a boot loader.

Regards

---

### Post by zieborn on 2021-03-09
Sorry for the slow reply. I'm not getting even a startup screen of any kind. Just the beeps and nothing on screen at any point.  Got some old memory around here somewhere that fits I think. I'll give that a try. 

Kubuntu on this system for a few years (not even sure). Kept updating forever, and really didn't need any help until now. I'm only trying to save it because it was so problem free for so very long a time. The PC is from, maybe, 2010. Ubuntu wasn't on it when I bought it, but I put this (or maybe originally plain ol' Ubuntu, I don't remember) on it way back then. I can't even remember now if Kubuntu was required at one point when Ubuntu got to be too much.

---

### Post by mastablasta on 2021-03-10
new ATX boxes mostly come without beepers, but old ones still had them. you can read the manual for motherboard to see what the beeps mean. they indicate a hardware error at boot.

in any case it is time for an upgrade. you can easily reuse the disks if they are sata.

---

### Post by guiverc on 2021-03-10
My PC is a 2009 dell, and it shows the POST (*power on self test*) results via blue LEDs on the front (which are numbered; you add up the numbers and you have your code). It will however use beeps for certain error conditions  if I recall correctly I discovered.

I have a more modern hp 8200 (*3rd generation i5*) and I know it has beep codes, as I regularly hear them when I turn it on (*it refuses to turn on because it complains about the PSU until I force it*)  *The 2009 dell is older as it pre-dates  the intel i-series cpus*.

---

### Post by CelticWarrior on 2021-03-10
In any case it's hardware, not Kubuntu.

---

