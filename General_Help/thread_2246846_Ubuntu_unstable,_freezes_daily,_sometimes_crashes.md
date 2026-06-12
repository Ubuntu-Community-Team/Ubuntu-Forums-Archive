---
title: "Ubuntu unstable, freezes daily, sometimes crashes"
date: 2014-10-03
forum: General Help
---

### Post by howeishotweb on 2014-10-03
My system is daily freezing at random times. It can be while gaming, watching video or web browsing. Image freezes, and sound loops. Rarely I can do the REISUB thing, but usually I have to do a hard reset. Very rarely, the system resets by itself.

Ubuntu is the newest one. 
Video card is a Radeon HD 7770, using the newest driver from AMD's website (supplied drivers caused catastrophic corruption with my dual monitors).
I have removed all overclocking, but it still freezes.
Any suggestions would be appreciated.

---

### Post by daniell59 on 2014-10-03
I had a similar problem. It turned out that the automatic memory setting were off. I set them manually and the problem was solved.

---

### Post by howeishotweb on 2014-10-04
"Automatic memory setting" ...? Are you talking about swap memory? That is turned on.

---

### Post by Bucky Ball on 2014-10-04
Which release are you using? 14.04 LTS by 'the newest one' I'm guessing. Perhaps a hardware issue, perhaps RAM? If things were working fine previously and this has developed 'out of the blue', I'd be looking there. Random freezes can often indicate dead or dying RAM or something more sinister. :-k

---

### Post by howeishotweb on 2014-10-04
Yes, 14.04.
There was never any problems while I had Windows on it.
I guess I can try running some ram check... is there any Linux tool for that? I don't have my boot USB anymore

---

### Post by Impavidus on 2014-10-04
At the grub menu, select the memory test. If you don't see a grub menu, press shift as soon as the bios screen clears, early in the booting process. Windows manages memory in a completely different way than linux. It's well possible that Windows never tried using that faulty piece of memory (if there indeed is a faulty piece of memory).

---

### Post by howeishotweb on 2014-10-04
Thanks. Memtest didn't find any errors, though.
Wonder what it could be, then...

---

### Post by pqwoerituytrueiwoq on 2014-10-04
how long did you let it run, i suggest no less than 20min

---

### Post by howeishotweb on 2014-10-04
It ran a single pass. That should be enough.

---

### Post by Impavidus on 2014-10-04
Sometimes it isn't. Memory problems might be intermittent. Some suggest running it for hours.

---

### Post by Bucky Ball on 2014-10-04
> **Impavidus said:**
> Sometimes it isn't. Memory problems might be intermittent. Some suggest running it for hours.

^^^
This. Get it running and go to bed. See if there are errors on arising. ;)

---

### Post by daniell59 on 2014-10-05
> **victorfhansen said:**
> "Automatic memory setting" ...? Are you talking about swap memory? That is turned on.

I should have been more clear. First I located the memory specs. Voltage, timing etc. The motherboard did not set them correctly. I manually changed them. Your memory can test can come back without errors, but if the voltage or timing is off, it can freeze the system.

---

### Post by howeishotweb on 2014-11-05
Okay guys I have been running Memtest since your last reply. [SIZE=1]Okay actually I only ran it for 4 hours. [/SIZE][SIZE=2]Still no errors.
And as far as I can see, all BIOS settings are optimal and standard.

I have installed Ubuntu on my laptop now as well and I have gotten a freezing there too (haven't used it that much yet). I'm pretty sure it's not a hardware problem.

Also I have upgraded to 14.10 (which screwed the AMD driver up, good times). Laptop installation is a fresh 14.10.
[/SIZE]

---

