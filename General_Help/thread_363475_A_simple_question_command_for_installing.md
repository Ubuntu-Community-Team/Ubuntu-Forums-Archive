---
title: "A simple question: command for installing?"
date: 2007-02-17
forum: General Help
---

### Post by GedDarkstorm on 2007-02-17
Well, xserver crashes when I try to install from the liveCD, but then I can get to the command prompt.

How, praytell, do I go back into liveCD without restarting the computer (which erases all the fixes I do from what I've found on the board)? In short, what's the command prompt for installing Ubuntu 6.10?

---

### Post by Qrk on 2007-02-17
The ubuntu installer is called ubiquity, so you can start it from a terminal with:

```
sudo ubiquity
```

But remember, its an X (graphical) installer, so it won't work if you don't have X windows (your gui) working. If you can't keep X up to run ubiquity, try using the alternate install cd, which uses the older ubuntu installer, which doesn't require X. The old installer is perfectly easy to use, just a less mouse intensive version of ubiquity.

---

### Post by GedDarkstorm on 2007-02-17
Ah, thank you very much!

Yeah.. I'm out of CDs.. I did have the alternative version, but it is corrupted. Nero just burned it to death I guess. Sigh, what can you do.

Well, thank you again for your help!

---

### Post by Gearhead61 on 2007-02-17
Hi guys, I'm new to linux in general, much less ubuntu.  I seem to be having a similar problem with the Xserver crashing when I try to install ubuntu.  I downloaded the ubuntu 6.10 iso image and burned it to a CD (is this the live CD or alternate CD version?  I couldn't quite figure out which one is which), but the Xserver crashed on me each time I tried to install it from the CD.  I am downloading the 6.06 version right now... is this the one that does not use Xserver?  Or is there something else that I need to do to get ubuntu to install on my machine properly?

I'm trying to dual-boot XP and linux so I can get a feel for linux before I fully commit to the switch.  I'm just sick of all the windows crap and want to try something new.  I appreciate any help y'all can give me!

---

### Post by aysiu on 2007-02-17
I would advise trying to reconfigure and then start the X server: ```
sudo dpkg-reconfigure xserver-xorg
startx
``` If that works, the proper command would be ```
gksudo ubiquity
``` not ```
sudo ubiquity
``` More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Gearhead61 on 2007-02-17
Thanks for the FAST response!  I will read that link over and then give it another shot!

---

### Post by Gearhead61 on 2007-02-17
Ok well that didn't work.  I went through the xserver configure menu series.  I picked the vesa drivers thing like I've seen here, but then when i try to do "startx" it says a fatal error occurred because a screen wasn't displayed or something along those lines... any ideas?

---

### Post by Qrk on 2007-02-18
hmm, thats odd. Usually vesa is the most stable driver. 
I'd just have to recommend the alternate install cd. Once you get ubuntu installed, you can install the binary graphics driver for your card, which should stabilize the X server.

Many distros don't use graphical installers percisely because of this problem.

---

