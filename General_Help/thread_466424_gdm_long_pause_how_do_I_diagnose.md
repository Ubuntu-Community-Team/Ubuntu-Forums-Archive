---
title: "gdm long pause how do I diagnose?"
date: 2007-06-06
forum: General Help
---

### Post by bugler on 2007-06-06
I have been messing with beryl and kiba-dock and compiling a bunch of stuff lately.  And I may have messed up something.  First off, I am a linux newb.  However, I have exclusively used ubuntu for the last 6 months or so.

I have a hp dv6435 ubuntu 7.04+beryl+awn.

Problem:  When I login  the screen goes to desktop, but that bar that loads I think sessions???? stays for a good minute before it clears and all appears to work normally.  The gnome panel is all greyed out, that is, application, places, system, are not seen... just a grey bar at top.  The big bar in the middle of the screen freezes, I believe when it shows the desktop icon.... not sure what you call that middle large part of the screen.  After a minute or so, all is well..
If I log out and log in.. same thing happens... If I suspend or hibernate, when I come out all is ok, no problems.

Question:  Where would I look to even start to diagnose this problem?  I would love to learn more about the inner workings.

P.S. beryl and Awn is NOT setup to run at start-up.

Thanks,

Bugler

Edited:  ISSUE RESOLVED.  I was running by some threads on ifconfig and was trying some different things and screwed my /etc/network/interfaces file.  I commented out everything except auto eth0 and auto lo.  All worked well after that.  I Love Ubuntu and Linux\\:D/

---

### Post by bugler on 2007-06-07
bump

---

