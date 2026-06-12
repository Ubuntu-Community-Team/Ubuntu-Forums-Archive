---
title: "ACPI Error keeps coming back"
date: 2020-10-17
forum: General Help
---

### Post by 27hreibspd on 2020-10-17
I keep getting this error on my computer, hopefully it is related to the problem I am having.

ubuntu kernel: [    0.047171] ACPI Error: AE_NOT_FOUND, While resolving a named reference package element - LNKA (20190816/dspkginit-438)

It started after I upgraded from 18.04 to 20.04, on my 10 year old computer, everything worked fine for awhile. Then the computer completely froze ALT+CTRL+T did nothing, the mouse didn't even move. I power cycled and got the above error, then booting stopped, and it dropped me into the command line. I tried a clean install of 20.04, everything worked for a while, then same thing. System freeze and now it won't boot. I had newer hard drive laying around, so for the fun of it I switched it out and installed again. Same thing. Next I booted from my install USB to try boot repair. It booted and then a couple minutes in it completely freezes. 
The computer is an old gaming computer AMD CPU with 2 NVIDIA GeForce GTX 570 GPUs. I can get the full specs if they are helpful.

I can't find anyone else with this problem, can anyone point me in the right direction for finding a fix? Is this hardware failing or something else?

Update: I tried going back to 18.04 since it might support my older hardware and so far everything is running fine.

---

### Post by metsikko on 2020-10-29
Hi,

I have a similar error coming up, but instead of LNKA it says '_PR_.CPU0'. For me the thing seems to work just fine, just very slow loading (Intel SSD Pro 1500 180Gb). I wonder if this error is even at the cusp of the issue, but being a bit of a noob on linux, it would be nice to hear from someone with good knowledge of the inner workings of the OS. What is the origin of this ACPI Error anyway?

As for the specifics of my case, I have a Phenom X4 955 Black on an ASUS M2NPV-VM (that is not 100% compatible). The internal graphics are no good at all, so I'm running a Quadro K2000.

---

