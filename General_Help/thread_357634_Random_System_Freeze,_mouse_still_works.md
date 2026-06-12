---
title: "Random System Freeze, mouse still works"
date: 2007-02-09
forum: General Help
---

### Post by TurkVU on 2007-02-09
Been having a problem for the last couple weeks where my system running Edgy will randomly freeze. I think it started around the time I installed an extra piece of RAM...but I'm not sure exactly.

Basically I can't trace it down to a specific app but it always happens when I'm actively using the system. Every window will just freeze...but the mouse will still move.

Any ideas how to start troubleshooting? I'm a pretty new ubuntu user.

Thanks.

---

### Post by jpeddicord on 2007-02-09
Try hitting Ctrl+Alt+Backspace when it freezes to check to see if X froze or not. If nothing happens, then it would be an X bug. If the screen flickers and brings you back to the login window, then you may have a faulty application.

---

### Post by TurkVU on 2007-02-10
Alt, CTRL, Backspace - AltCTRLDelete and Ctrl/ESC don't work...so it seems to be an X issue.

---

### Post by raydekok on 2007-02-10
do you have a wireless pci card?

---

### Post by katiad on 2007-02-10
I've had the same problem. Turned out to be faulty ram. I thought it was a graphics card / X problem for ages. Used to get two kinds of freezes (one where the mouse would work but nothing else would - and one where /everything/ would freeze) - and also, the system would periodically dump me back to the login screen as if I'd ctrl-alt-backspaced. Couldn't trace it to anything, but it was when I was actively using the system. 

Memory tests all turned up OK, showed no errors. Eventually, on a whim, I replaced the memory with one from another computer. All problems gone.

Except the other computer, the one with the old memory... well, it died rapidly, and I ended up having to do a complete format/install. (It was windows.) 

Try removing the new ram stick you just put in. If the problems go away, you have the answer.

---

### Post by jpeddicord on 2007-02-10
Were/are either of you (katiad and TurkVU) mixing memory sizes? For example, were you using a 1GB stick and a 512? I know my older PC had some minor problems with mixed sizes, but I never thought it would lead to freezes.

---

### Post by jschavey on 2007-03-21
I'm having the same issue.  Everything seems to simply stop responding.  The mouse moves, but nothing responds.  If I have a CD playing it'll finish playing the track and then stop.  If I'm streaming music, it will continue for hours, but never start responding again.  I have only one stick of memory which is fairly new so I don't think that's the problem.  The problem usually occurs if I'm switching between tasks often.  This is making it completely impossible to work.  Any news?
Edit:  Ctrl+Shift+Backspace does not work either.  And yes, I do have a PCI wireless card, but I don't use it.

---

### Post by daspooky on 2007-03-30
jschavey,

This is the exact same issue I am experiencing:

- keyboard not responding
- mouse still movable but not responding to clicks
- music continues to play

I'm not sure it could be related to wireless as I'm running Ubuntu in a virtual machine (VMWare). My laptop uses wireless but the Ubuntu sees it as a regular network connection...

It's a very sad thing. I hope more information on this issue will be available soon... I'll keep searching for it. I really don't want to switch to another distribution.

---

### Post by Hallvor on 2007-03-30
Have the same problem. Mouse cursor moves, but I can`t click anything. (The keyboard seems to work, though!) Has happened to me when I`m busy and click between different desktops.

---

### Post by Digitallysick on 2007-04-01
i have this issue in feisty fawn, most of the time when my screen goes to sleep, it wont "wake up" the mouse will just move, everything is froze, it also happens at other random times when the pc is "awake"  where in the logs can i check to see what causes this? Rebooting linux 4 times a day isnt a good thing

---

### Post by schilcha on 2007-04-01
Me too! Edgy froze from time to time and lately every five minutes. There were no problems running without X. I got hold of a knoppix-live-cd and even had the same freezes there!

It turned out to be a broken graphics-card or video ram. My laptop now runs stable with the vesa driver instead of an nvidia-specific driver (nvidia and nv caused the system to freeze). However, with vesa I have severe pixel-flicker on the lcd (depending on tempreature and pressure on the laptop), which tells me that the graphics-card is somehow broken.

---

### Post by Digitallysick on 2007-04-02
i know its not my graphics card/ram all worked fine in xp and vista, for almost a year. Just doesnt seem to work in ubuntu =( Happens at random

---

### Post by dadsvideofix on 2007-06-06
I have the same problem, it also happens on windows also. I just upgraded to c2d 4400. I only have about 2 days left on the RMA #. Not sure if it is CPU or memory.

---

### Post by Bastaard on 2007-07-09
I've got the same problem in feisty: system freezes from time to time. Running feisty with the newest compiz fusion, ATI Radeon graphics card, 1000MB RAM, ~250MB swap, Speedtouch USB WiFi dongle through ndiswrapper, Audigy 2 sound card... For me, the mouse keeps moving but everything else stops (including music). Never happens in Windows XP.

Is there any way I can check why the system froze? Like in a log file or something? Any help would be appreciated as I'm afraid I have to go back to Windows otherwise :(

---

### Post by soulglo83 on 2007-07-20
im running feisty with a intel core duo 4400, an elitegroup nf650islit-a mobo, 2gb of good name brand ram (Forget @ the moment) and a MS comfort curve 2000 keyboard.  About 20 - 60 minutes after booting my computer will continue running animations and processing the movement of a mouse cursor, but nothing else.  ALT+CTRL+ Backspace or any of the F keys doesn't work.  Even turning caps lock off or on doesnt work (so the alt+sysrq commands dont work).  This only happened after I freshly installed feisty, it did do this when i upgraded from edgy with my previous install.  Anyone have any idea what program or anything could have introduced this (show stopping) bug?  I will look through my /var/log/Xorg.... log when it happens again.

EDIT:  I forgot, I'm using the ati fglrx drivers for my X1600 PCI video card

---

### Post by upthelum on 2007-07-20
I had issues like this and had a wireless card, which i also didnt use but when i tried removing it, it seemed to solve other problems too. I have heard that there can be issues with wireless cards and Linux so i would give it a try.

---

### Post by fredj on 2007-07-21
I had this random freeze where I could move the cursor but not click on anything. I cured it by updating the firmware on my DVD drive.

---

### Post by highd1 on 2007-07-21
I have tried updating drivers with no luck and I am still experiencing a freeze but my mouse still works.  there is this wee little pixel that appears right above the mouse cursor when it happens.  I have toured all around looking for help and still no answers.

---

### Post by marx2k on 2007-07-27
I am also experiencing these random freezes and have only started to last night. I can make it happen at will but eiither running 'compiz --replace' or 'metacity --replace' 

I am running Feisty in an AMD Athlon XP 2000+ with 1GB of RAM that passes memtest 

Everything gets frozen except my mouse will still work flawlessly.  But at that point I cannot get to a TTY term or even reset X to test what may be the culprit causing these freezes - obviously it's something with the window manager, but how to find out WHAT?

---

### Post by subtex on 2007-07-29
> **raydekok said:**
> do you have a wireless pci card?

I do.  Is this one of the known causes of this bug?

---

### Post by j-lo on 2007-08-09
FWIW marx2k, I'm experiencing the same kind of freezes that you do...

I just swiched to compiz fusion from beryl, running feisty with trevinos latest compiz packages (from jul 31 I think). This is the only version of compiz fusion I've tried. 

I can make the system freeze (with mouse pointer moving) by doing compiz --replace or metacity --replace or by trying to change the compiz settings using ccsm or gconf straight. Pretty sure it's a compiz problem, since nothing else has changed.

Running on a laptop with Intel Core Duo and Intel graphics.

juhis

---

### Post by subtex on 2007-08-09
I took my linksys wifi pci card out and now my system is stable.

I guess I'll have to deal with a long wire running through the hallway for now.  At least until the next full Ubuntu update.

---

### Post by sidimaiga on 2007-08-12
> **subtex said:**
> I took my linksys wifi pci card out and now my system is stable.

I guess I'll have to deal with a long wire running through the hallway for now.  At least until the next full Ubuntu update.

Hi, 

Is there a workaround that fot people like me who  can't remove my Wifi card? It&#347; my only access to the Net.

Thanks,

---

### Post by Digitallysick on 2007-08-13
All the info you could want on this, is on my big post here, 

[http://ubuntuforums.org/showthread.php?p=3181025](http://ubuntuforums.org/showthread.php?p=3181025)

---

### Post by Bastaard on 2007-10-04
I found my problem was because of a failing GPU in combination with compiz fusion, the same problem exists in Windows when running games. No blame for Ubuntu there! Gotta buy myself a new one.

---

### Post by VMbuseck on 2007-10-09
I have this issue in kubuntu 7.04 feisty fawn.

AMD Duron 900
512 MB RAM
NO wireless
GeForce2 MX 64 MB

The system works fine with Win2K.

A similar system with a Duron 1300 works without freeze.

I've removed powernowd without success to the freezing issue.

:mad:

---

### Post by erikcw on 2007-10-16
I was also having the problem with Feisty.  I upgraded to the Gutsy RC in hopes that newer packages would solve it, but no luck - still random freezes.  Gnome also seems to randomly restart.

---

### Post by isaaclimdc on 2007-12-02
Same for me. I always have to force shut down. And when I do, it always does a check for disk errors on the next startup that wastes about 2 minutes. Anyone have any ideas?

---

### Post by VMbuseck on 2008-02-24
Two of my desktops (one 700 Mhz Celeron with dapper, the other 900 Mhz AMD with feisty) still freeze randomly. Both computers has a GeForce2 Graphic card. The driver is "nv".

Does anybody as a solution for this problem ???

---

### Post by VMbuseck on 2008-03-08
Along to a hint from the german support forum I installed the nvidia-glx package and set up die driver "nvidia" instead of "nv". The problem seems to be solved.

---

