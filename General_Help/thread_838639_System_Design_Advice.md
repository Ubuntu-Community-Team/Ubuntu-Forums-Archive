---
title: "System Design Advice"
date: 2008-06-23
forum: General Help
---

### Post by Locky1138 on 2008-06-23
i'm building a new system from scratch, and it promises to be a monster.  It will need to run adobe apps, and video-editing apps, many of them, simultaniously.  the user i am building it for HATES windows, and is sick of Mac, so Ubuntu will be the primary OS.

my plan so far, is to run ubuntu, and wine/VM windows to run the apps she needs.  i'll duel-boot if that fails.

the hardware specs i've laid out so far are:

AMD Phenom 9750 2.4GHz 4-cores
8gig Corsair dominator dual chanel 1066
Gigabyte GA-M750SLI-DS4 mobo
GIGABYTE GV-NX85T512HP GeForce 8500

i am up in the air as to whether i want to liquid-cool and overclock it.

so, what do you all think, will there be enough processing power to VM windows, or Wine the applications she needs?  will i be stuck booting into windows to run those apps for lack of power, or other reasons?  are there any pit-falls in this plan that i've just completely missed?

thanks in advance for any/all help, comments, etc.
Locky

---

### Post by bubba_169 on 2008-06-23
That might *only just* work (note the sarcasm)!

Should be easily enough... :D

---

### Post by Locky1138 on 2008-06-23
if i can take that sarcasm to mean "Complete over-kill" then thats good.  over-kill is my goal.  i want it to work, run fast, and last a few years at least.

---

### Post by rainwalker on 2008-06-23
I'm not the most knowledgable about hardware, but I think you need a 64-bit OS to take advantage of all that RAM, right? And from what I've read, 64-bit Ubuntu can be a real hassle sometimes

---

### Post by Locky1138 on 2008-06-23
i'm running ubuntu on an old AMD 64 bit single core right now... it has never given me any problems... well nothing serious at least.

---

### Post by tamoneya on 2008-06-23
looks pretty good.  I am looking to build a similar system (same processor less ram) pretty soon as well. A couple recommendations:
1.  Use the coolermaster centurion 5 case.  I have used it several times and is an amazing case and not expensive.
2.  If it is going to be a higher end media processing rig I would add some sort of RAID probably RAID 1.  It will improve system performance and be good when you are working with large files. Its very expensive(relatively) to do this through hardware so you can do it as a software raid with mdadm.
3.  You can also overclock pretty well without a water cooled system.  Go with a nice air cooler and you should be able to get 2.8-3.0 Ghzish clock speed without much of a problem.

---

### Post by Twintop on 2008-06-25
That setup is similar to what I'm running (Phenom 9600 BE, 8GB DDR2-800 RAM, 256MB 7900GS but has been an 8600 GT), and I can tell you that IT IS overkill. The great thing about it is, though, that I can have multiple VMs running at a time, each with a dedicated core (by using taskset) and each with 1GB+ of RAM dedicated to it. Other than that (and BOINC or Folding@Home), it really is overkill....

---

### Post by fjgaude on 2008-06-25
I'd go for quiet and no water.

What you propose will more than do what she will ever need.

I'm a graphic designer and find what I have more than enough, 4GB RAM and dual core CPU, overclocked with a good cooler:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=24C; under max load, temp=41C, fan=1167 RPM; VCore=1.39/1.38v:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   18948 MB in  2.00 seconds = 9487.52 MB/sec
 Timing buffered disk reads:  644 MB in  3.00 seconds = 214.42 MB/sec
```

Under VMware the Windows apps are fast and quick, no delays. The raid5 array helps with its thru-put. Notice my signature.

---

