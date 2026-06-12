---
title: "Systems hangs for a bit every few minutes."
date: 2007-05-11
forum: General Help
---

### Post by lumzy on 2007-05-11
My specs are as follows:

Feisty Fawn running on:
AMD Athlon XP 2500+
1GB Ram
50GB or so FREE HD space
ATI Radeon 9600Pro

Keep getting some odd slowdown, whether I'm running WoW, or browsing the web, or using OO.org, it doesn't seem to matter.  Every 3-5mins or thereabouts, my system will bog quite heavily for 3 or 4 seconds, and then pop back up to normal speed. 

As I've said, it doesn't seem to be 3D related, and slowdowns occur whether or not Beryl/XGL is active or not.  I have my latest ATI FGLRX drivers installed and working properly.  I was just wondering if anyone else had experienced similar 'random' slowdown issues, and what they did to alleviate the problem.  It does get quite annoying and is fairly consistent. 

I've tried various tweaks, but to no avail.  Also, this is not a new problem, it seems to have had the consistent slowdown from the initial installation.  Thanks for your insight.

---

### Post by vav on 2007-05-11
Keep a terminal open with 'top' running... as soon as the slowdown occurs, check which process is problematic. Unless the computer freezes completely, the rogue process should show up

---

### Post by lumzy on 2007-05-11
Alright, did what you said.  While playing FretsOnFIre (I used this to test because the slowdown is VERY noticeable in this game), I kept a terminal open with top running, and the game was usually on top of the list, as I assume it should be.  But, when the slowdown occured, Xorg shot to the top of the list during the lag, and then resumed its normal position afterwards.  Any idea what would be causing Xorg to periodically consume much more processor power for ~5 seconds every few minutes, so much that it lags everything else to a near unusable state during those few seconds?

---

### Post by lumzy on 2007-05-11
Just an update for anyone who may encounter a similar problem:

Kept noticing that also close to the most used resources in top, would be events/0 when the lag spike occured.  I did some googling and came to the conclusion that some piece of hardware was causing the issue.  Had a look at dmesg output and noticed "scan started.  scan complete."  

While trying to decide what this meant, it dawned on me that I still had installed an old, generic, and somewhat crappy wifi card in a pci slot.  I didn't notice at first because in Windows XP it had always been disable and hadnt caused any problems.  I removed the card, and upon the next boot, did some more testing.  I believe my problem is solved, and I answered my own  question.  :)   Thanks.

---

