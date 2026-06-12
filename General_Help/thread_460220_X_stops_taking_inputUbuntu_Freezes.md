---
title: "X stops taking input/Ubuntu Freezes"
date: 2007-05-31
forum: General Help
---

### Post by Draek on 2007-05-31
Hey everyone. This is a problem I've seen many people post about in the "Ubuntu Freezes" posts but its getting all mixed up and noone is paying attention to the symptoms.

Sometimes people write posts about "Ubuntu freezes (hard locks) and i can't move my mouse, and have to reboot".

Keep in mind this is QUITE different than "Ubuntu freezes, I can still move my mouse, but my comp doesn't take input and I have to reboot."

I've been using Fiesty since its release. I've used it on 3 computers, the first computer had major issues with it, I would get hard lock freezes constantly. This ended up being a problem with the PC hardware, bad RAM etc.

Then I switched to an older PC, a AthlonXP 2600+ with a GeForce4 and 1.5GB of ram and a nforce motherboard. I've not installed any drivers other than the defaults that come with a new Ubuntu install. So therefore no NVIDIA drivers, etc.

Seems if i drag a screenshot (with preview showing) or a movie within nautilus, or if I'm playing a song in Banshee and try and resize the banshee window; Or perhaps I could be in GAIM, switching tabs or resizing the chat windows. Any of these scenarios can cause X to freeze, and stop responding. Of course the MP3's still play, MSN still shows me online and I can still SSH into my computer. So I know its X that's buggered, or at least thats what it looks like.

Has anyone experienced this type of problem in the past? Or perhaps still experiencing this problem? Please write some comments and let it be known in this thread so we can have the masterminds of the forums comment on some solutions.

---

### Post by BigErn on 2007-06-09
Seems no progress has been made on this issue.  I have it in Feisty with my Radeon 9800 pro.  I have it in Gibbons (next Ubuntu release) with my Radeon 9800 pro.  I bought a new video card- an Nvidia Geforce 6600.  Still there.  I've disabled on board LAN, sound, and Hyperthreading in the BIOS - still there.  Many other people are having this problem.  I don't think it's a defective hardware issue.  I think this is a bug, but I have no idea how to delve deeper, since there is nothing in any log file to indicate a problem.  I'm at my wit's end. I might have no choice but to reinstall Windows  :(

---

### Post by imdano on 2007-09-18
I have a similar problem, but I've only reproduced it when trying to resize a window by dragging it from the bottom edge.  The mouse still moves and I can ssh in, but it won't respond to the keyboard or clicks.

I've searched around a little but haven't found any formal bug reports on it.  Anyone know if there is one out there somewhere?

---

### Post by ZMEZman on 2007-09-19
Yes, I've had this problem also...I have a g-Force 6800 512MB video card. I put the CD in and everything booted up fine I ran a couple programs, and decided to install Ubuntu 7.04. After I installed ubuntu I ran a few programs ...got online downloaded some updates... and then it hard froze..I turned off my PC by using the power switch, booted it back up right away. And It ran longer but still hard froze again and every time I reboot my machine it stays on longer...I've rebooted like 15-20 times anyway, I think that is the only way to fix the problem...Keep it running till it freezes again, then push the reboot button...[-o<

---

### Post by evilpuffball on 2007-09-19
I have a similar problem as well.  Mine was the result of CUPS running amok though.  (Seriously, all I was trying to do is share a printer, but nooooo.)  And now thanks to having to use the power button to force a shutdown, I can no longer log in. :-/  I'm thinking of trying the 6.06 LTS version instead of 7.04 which has given me nothing but problems lately.

---

