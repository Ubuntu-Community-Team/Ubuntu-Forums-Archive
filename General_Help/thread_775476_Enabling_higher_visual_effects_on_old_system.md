---
title: "Enabling higher visual effects on old system"
date: 2008-04-30
forum: General Help
---

### Post by sbonner on 2008-04-30
I can't get visual effects to enable.  It is stuck on "none" in the appearance preferences interface, visual effects tab.  When I try to move to normal or extra, I get an error message;
"desktop effects could not be enabled"

I think I have a powerful enough system to run them:
Intel Celeron(P) 340 2.93 GHz
750 Meg RAM
integrated (i.e. sucky) graphics - Intel 845GV

The graphics card is not among those listed at 
[http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL) 

Am I out of luck, or is there some way to force the system to try the card, i.e. not check against it's list of supported cards, to see if it can run the graphics anyway?

This is the first step in my attempts to get compiz running at full power (only a few feeble effects work right now, and I think I need to be in normal or extra mode to try out more).  Eventually, I want to get AWN dock.  If I fail in that, then I'll try out SimDock, but I'd like to find out what the limits of this old box are, first.

Thanks for all help!

---

### Post by klange on 2008-04-30
You don't use XGL with an Intel card.
Run 'compiz' in a terminal and post the output, as the card should work fine.

---

### Post by sbonner on 2008-04-30
I will run compiz when I get home from work tonight (about 9:30 ish, US central time) and post the results.  Just run "sudo compiz" from the terminal?  It is doing some of the lesser effects (minimize effects and such), but none of the good ones.

In the meantime, any idea why I can't move out of "none" in the visual effects tab?  Might that have to do with my graphics card not being recognized via a compatability list?  The error message is uselessly vague, so I'm making a "stab in the dark" to guess the problem.  :)

Thanks!  More to come tonight.

---

### Post by klange on 2008-04-30
> **sbonner said:**
> I will run compiz when I get home from work tonight (about 9:30 ish, US central time) and post the results.  Just run "sudo compiz" from the terminal?  It is doing some of the lesser effects (minimize effects and such), but none of the good ones.

In the meantime, any idea why I can't move out of "none" in the visual effects tab?  Might that have to do with my graphics card not being recognized via a compatability list?  The error message is uselessly vague, so I'm making a "stab in the dark" to guess the problem.  :)

Thanks!  More to come tonight.

Just "compiz", no 'sudo'.

---

### Post by sbonner on 2008-04-30
Output from compiz:

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

