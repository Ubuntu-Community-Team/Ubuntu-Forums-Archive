---
title: "Why is my ubuntu so slow..."
date: 2007-03-11
forum: General Help
---

### Post by berlinbrown on 2007-03-11
The ubuntu desktop with my machine is so unresponsive.  Clicking on folders or opening applications take on an order of 20-40 seconds.  It could be my cheap hardware configuration which I will change.  But, just wondering if there is something that can be done.  I mostly use Firefox and Eclipse for development.

Current config:
Via Cpu (cheap I know) 2Mhz
Ram: 1gig
Via 3D 64Mbit AGP graphics card

Will upgrade to:

Asus AMB Sempron 3.2Mhz
Ram: 2gig
Nvidia Video Card.

I think it is the via cpu.  My 800mhz intel is more responsive.

---

### Post by schilcha on 2007-03-11
I'm running ubuntu on a  1.4GHz Pentium4 Mobile notebook with 512MB RAM, which as absolutely more than sufficient.

In my experience, disabled dma-mode on your hard-drives can slow your system down considerably. 

Issue the command "sudo hdparm -v /dev/hda" (replace hda with your harddisk) and look, if the parameter "using_dma" is set to "on". If not, you definitely should aim at turning it on. 

If that doesn't help, run "top" in a terminal to see, if something is eating up your memory or your cpu.

Good Luck!

---

### Post by berlinbrown on 2007-03-11
You think the CPU makes a difference:

"1.4GHz Pentium4 Mobile"

[http://ubuntuforums.org/showthread.php?p=2215514](http://ubuntuforums.org/showthread.php?p=2215514)

---

### Post by schilcha on 2007-03-11
Sorry I failed to make my point clear:

I think, my system is weaker than your's, but is strong enough to run ubuntu all right. (I even run xubuntu on a 400MHz PII, which is still sufficient to surf the internet).

I think, your system should manage to run ubuntu like a charm. 

What I did susgest was to check on your harddrive-settings.

---

