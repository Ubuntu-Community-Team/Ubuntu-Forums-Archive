---
title: "Gusty freezing stops responding."
date: 2007-11-03
forum: General Help
---

### Post by leona on 2007-11-03
Hi there

I did do a search for this but couldn't find an Exact match so I thought I'd post a new one, sorry if this was the wrong thing to do.

I have upgraded to Gusty 64bit, from Fiesty 64bit.

Have installed Nvidia restricted drivers, using Compiz Fusion and the cool desktop effects.

(just thought I'd mention it if it helps identify the problem).

CPU is running at normal temps.

When I'm surfing with Firefox or editing a document with Open office. the system will suddenly stopped responding, now this is odd, because I can move the mouse around, but can't perform any actions, can't click, the screen appears to keep updating, as the monitoring graphics still update, but no action on the mouse or keyboard will do anything, the caps lock, num lock lights will not go on or off, Ctrl+Alt+Backspace do nothing, can't 'drop to a shell', nothing. only thing I can do is hit the reset button.

Now I thought if it was a system freeze then everything would stop working, but it seems odd that the screen seems to continue to update and I can move the mouse pointer around, just I can't 'do' anything with it.

Now I'm guessing this might be a compiz thing as its one of the new features I've used since Fiesty, are they're known bugs with it that cause this issue?

Its a shame to see stability issues creeping in to Linux, as its one of the reasons why I turned to Ubuntu, for a stable reliable platform.

---

### Post by Mithrilhall on 2007-11-03
I was running the nvidia restricted drivers and had the same issues so I removed them and I'm still having the same problems. I'm not using compiz or anything out of the ordinary.

I haven't searched the forums yet but hopefully there is a solution.

---

### Post by leona on 2007-11-03
Ok right well that seems to rule out both the Driver and Compiz theories then, drat, what else could be doing this?

---

### Post by Mithrilhall on 2007-11-05
I'm going to keep poking around and I'll post anything I find.

---

### Post by Melcar on 2007-12-06
It seems I have a similar[ issue]("http://ubuntuforums.org/showthread.php?t=568023&page=2").  I'm also running 64bit Ubuntu.  I'm going to try the 32bit version and see if I have the same problem.

---

### Post by TapocoL on 2007-12-12
I have experienced the same thing. At first, I thought it was just some random freeze up, but it has happened several times now. I am on Gutsy as well. Im on a compaq presario V2135US. One difference is my mouse does not even move more, but a couple times it was while I was surfing with Firefox and the mouse just stopped moving while the page was finishing loading. I cannot do anything, my sound quick keys stop working. The synaptic mouse pad stops working, but the light remains on and it will not toggle on/off. The only button I have found to work is the power button, which on click will bring up the shut down options on the screen, but I still cannot select anything. I have had to shut down manually and reboot.

I haven't upgraded my laptop, here are the specs on the V2135US:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00284954&lc=en&cc=us&dlc=en&product=449396&lang=en#](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00284954&lc=en&cc=us&dlc=en&product=449396&lang=en#)

Hopefully, someone can locate a consistency is this bug.

---

### Post by alapidas on 2007-12-20
I have been suffering from the same problem on a 32 bit. (64 bit hardware)

---

### Post by anand_gs on 2008-01-07
I have the same problem on Kubuntu Gusty Gibbon x64. I upgraded my laptop (Compaq Presario R3000) from Feisty to Gusty. Whenever I try to run Firefox the screen just freezes and it does not take any kind of user input. 
Out of curiosity I decided to use kernel 2.6.20.16 instead of 2.6.22.14 during Grub startup. Surprisingly I did not have the freeze problem. I've been running Gusty like this for more than a month and I have not encountered any problems with it yet. The problem may be in 2.6.22.14 kernel. I'd like to try installing a new kernel from kernel.org and try it out, but since I'm new to Linux I'm afraid I might screw up my machine. Can anyone try it out?

---

### Post by jfdill_2 on 2008-01-07
I've been having similar problems on Gutsy 32bit and from the debugging that I have done so far Firefox seems to be thrashing when this happens, taking up > 90% of the CPU.  Previously, I have had problems with Firefox running animated GIFs with no delay between frames, so I tried changing the option to run animations "once" but that did not fix the problem.  This problem occurs on a Dell Optiplex GX260, but my Averatec laptop does not have this problem.  Also, I do not have this problem with Opera browser.

Update:  I found this page about firefox freezing with pop-ups and Google Toolbar, and am now able to reproduce the problem by trying to open a pop-up window.  I don't have Google Toolbar on my Averatec, which would explain why I don't have this problem on my laptop.  My guess is that maybe it has something to do with the popup blocker function of Google Toolbar.  I'm going to try removing Google Toolbar and see if that fixes the problem.

[http://www.plasser.net/blog/archive/2007/11/27/ubuntu-firefox-freezing-on-popup-solved](http://www.plasser.net/blog/archive/2007/11/27/ubuntu-firefox-freezing-on-popup-solved)

Confirmed!  I removed Google Toolbar and the problem went away.  Just to make sure, I installed Google Toolbar again and the problem came back, uninstalled and the problem was fixed.

---

### Post by mouser on 2008-01-07
I have been experiencing some of the same problems. It seems to occur more frequently when my wife is on Firefox checking her Gmail account. I thought it might be the nvidia drivers at first, but it sounds like that might not be the case. I also thought about the flash issue, but I've uninstaled it and it still seems to freeze. I'm not sure that I have much to offer, I'm only a casual Linux user. I will try to keep up on this post and I'll try anything that might help.

---

