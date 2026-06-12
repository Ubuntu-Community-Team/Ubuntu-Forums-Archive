---
title: "LiveCD Incredibly Slow to Boot"
date: 2005-04-26
forum: General Help
---

### Post by jsavage on 2005-04-26
This is my first experience with Ubuntu,  Kubanu in fact because I couldn't get the plain Hoary version to load.   I have validated the MD5 so the CD is correct.  My main complaint is that it is far to slow to be usable.  This is on a PII 266 with more than 128 MB Ram.   Yes, I know this is not a high spec machine but  I have used so may other live cds that I have lost count and this is by far the slowest.  At a guess 10 minutes between startx and the UI Menus becoming available so about 15 minutes altogether.    Now having booted, the menus apear sluggish - I hate to say it but a bit like win 98 when full of malware and low on memory.

I would be happy to extract a log file if someone would tell me how and where to send it but I suspect this is not just me but a core problem with the software architecture.  Afterall - all other Live CDs that I have tried have booted much more quickly.

Before I try and install to a hard disk, can anyone put hand on heart and say that they have experienced the same with liveCD and have had a good experience with a HD Install ?

Please don't misunderstand me.  I am a great supporter of OS software and the Ubuntu concept.   I want it to suceed.  

James

---

### Post by Hinko on 2005-04-26
Your software is kinda slow, I wouldn't recommend installing kubuntu on it regardless of how the live CD works. Anyway, if for instance knoppix is a lot faster on your machine, it could also be the case that your CD player has difficulty reading the disc (noticeable by the sound of an out of control spinning disc :-s ). 

either way, 128 mb ram and the system you described are not a lot and Kubuntu is quite heavy with everything that's loaded into your memory. It has to run a system, KDE 3.4, openoffice, etc, etc. So from my comfortable armchair and behind a fast PC I'd say 10 minutes sounds reasonable..

---

### Post by jsavage on 2005-04-26
Knoppix is much faster.  Strangly, the CD is noisier/ faster under Knoppix but does not change speed drastically for either.  

James

---

### Post by angrykeyboarder on 2005-05-07
[QUOTE=Hinko]Your software is kinda slow, I wouldn't recommend installing kubuntu on it regardless of how the live CD works. Anyway, if for instance knoppix is a lot faster on your machine, it could also be the case that your CD player has difficulty reading the disc (noticeable by the sound of an out of control spinning disc :-s ). 

either way, 128 mb ram and the system you described are not a lot and Kubuntu is quite heavy with everything that's loaded into your memory. It has to run a system, KDE 3.4, openoffice, etc, etc. So from my comfortable armchair and behind a fast PC I'd say 10 minutes sounds reasonable..[/QUOTE]

Heck, I thought it was slow and I'm working with 1 GB of RAM.... ;-)

---

### Post by ssam on 2005-05-07
the live cd has to make a ram disk to run which will eat quite a bit of you 128mb, leaving not much to load actual programs into. when you run out of ram everything slows to a crawl. can you install some more ram?

if you did an install it would probably go a bit faster. but on that spec machine you dont want to be running kde or gnome. xfce or one of the lighter window managers might be faster.

---

### Post by roland on 2005-06-03
I think it is not only the amount of RAM, but also the cloop filesystem. I have tried the Ubuntu Live on a Pentium II 233 with also 128 MB RAM, and it took even longer than 15 minutes to fully load GNOME. The RAM memory will be filled with the ramdisk, but the processor has to unpack the cloop system. Cloop is not the fastest compression you can think of.

And, as ssam said, running KDE 3.4 is not a very good idea on a Pentium 266, although I have a Pentium II 350 at home running KDE 3.3 quite smoothly. Maybe because it has 192 MB RAM and is not booted from a Live cd...

---

