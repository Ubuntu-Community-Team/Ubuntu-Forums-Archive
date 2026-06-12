---
title: "Compound Question: What on EARTH is going on?"
date: 2007-04-26
forum: General Help
---

### Post by lovloss on 2007-04-26
I am having a nightmare trying to use ubuntu (kubuntu really), I never had this much trouble with it before. Im going to list all the problems im currently having so that the scope of the issue can (hopefully) be recognized as boiling down to one or two major flaws on my part.

 This is a new computer, with a nice mobo, an ATI RADEON X700, 1 gig memory, and a 300 gig SATA HD running off a SATA card. The architecture is 64 bit (AMD ATHLON).  I built the thing myself, and it works mighty fine with windows (ew, that hurt to say). The linux I just installed is Kubuntu Feisty Fawn AMD64. It runs dual boot on partition 2 of my SATA.

Problem 1:  The VESA driver causes my monitor to blink out as if it loses signal. Research showed me that others with Radeon X700s had the same problem. I can get in with fglrx, except it seems that the splash loading screen for kubuntu starts out in VESA regardless of xorg.conf. In other words, I have to log in and select 'recovery mode' each time, load it up, then type 'kdm' in order to bypass the loading screen and make it to the desktop. I probably shouldn't have to do that.

Problem 2: Nothing is automounting. No matter what I stick in or whaere, all USB devices are being ignored. I have to manually make a mount point each time, and it tends to mount things without giving me any permissions when i do that, making use of USB disks a nightmare. What's up with that?

Problem 3: Kaffeine and movie player won't play movies. They just show the bar moving and a blank square. Same with music. VLC does work, but thats it. I did do all the proprietary format stuff, including the use of medibuntu.

Problem 4: I cant rip cds. In fact, although i can play and load media on cds, the sound juicer claims it detects no cd rom devices. Im assuming this is part of my mounting problem...


So um.... yeah, any help would be appreciated.
:guitar:

---

### Post by zvacet on 2007-04-27
First looks like drivers problem but I´m not an expert.try t ofind and install drivers for your video card and 

```
sudo dpkg-reconfigure xserver-xorg
```

and pick your graphic card

For second system>settings>removable drives and media(it is for GNOME but must be something like this in KDE)

That is all I can think of.

---

### Post by lovloss on 2007-04-27
Problems 2 /is solved. I needed to reinstall PAL. I already tried to reconfigure xserver-xorg for problem #1 and it didnt do anything. I am in fglrx when im on my desktop, its only the loading screen that kills the monitor, which is why i have to go around using recovery mode.

---

### Post by Smuve on 2007-04-27
You might be able to swith to a text boot and avoid the splash screen.

In /boot/grub/menu.lst

delete quiet and splash at the end of your kernel line

---

