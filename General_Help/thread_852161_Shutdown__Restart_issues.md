---
title: "Shutdown / Restart issues"
date: 2008-07-07
forum: General Help
---

### Post by blackhatbrigade on 2008-07-07
Alienware M9700
nvidia 7900GS SLI
RTL wifi card
Ubuntu Hardy Heron

I'm having issues with getting my system on and off.  I've been fighting when I power on with what I thought was nvidia issues, as it will sometimes start and everything goes great up until X starts, then I get the blank screen that is usually a problem with Linux picking the wrong card to send the display to.  However, I'm not so sure that's what is going on now (not saying it isn't, just not sure).  I can get the system up and going if I switch to terminal and restart (works every time, no clue why) or just hit the power button (which is set to just turn the system off on my setup).  I did fight with my nvidia setup on first install.  I ended up using the EnvyNG utility to get it fully up and running on the "nvidia" driver.  I'm familiar with the usual issue on these laptops of setting BusID "PCI:7:0:0" and that option is currently set.

Shutting down is a little more problematic.  I can't pinpoint a solution to it.  I'm having several problems that could be causing it I think.  First is the wireless setup.  I'm using the NDIS wrapper and everything goes pretty well, unless I leave the system on for about 2 days straight.  Then the wireless stops and I have to reboot.  The problem is, that if I just reboot I get the blank screen problem, although the system does go down just fine before it comes back up to a blank screen (right at X initialization).  I can get X to come back up just fine if I go to shut down first, but that's where I hit the problem where it may just freeze and not shut down at all.  Mouse still moves, but I can't get anything else to respond.  I've been forgetting to try ctrl+alt+backspace or ctrl+alt+f2 to shutdown.  I'll try that next time to see if it's a work around for now.

I don't know if it's related, but I have been having issues with windows locking up.  Not freezing the computer, but I've hit a point where any new X app I try running starts up then grays out and is unresponsive.  Maybe a CPU usage issue?  But all my existing windows work fine, so I'm confused.  This doesn't happen often and usually is only when the system has been running for while (couple days).

I'm really sorry for the multiple issue question, but I don't know how to break this one down.  It seems like about 3 or 4 things all screwing up together.

---

