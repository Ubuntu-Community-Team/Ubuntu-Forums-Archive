---
title: "Ubuntu Feisty -- becomes slow 1-2 over days"
date: 2007-04-28
forum: General Help
---

### Post by adam_lw on 2007-04-28
Greetings all, from a new poster (but fairly experienced user)-- 

I hope someone can help with a baffling slowdown issue.  I'm running Ubuntu 7.04 on an IBM P4/2.4 with 1GB RAM and 320GB storage.  The system runs very well on a clean startup, but eventually becomes uselessly slow.

The slowdown generally takes about 1-2 days to happen.  It seems an all-or-none proposition, i.e. that the system is either running well or poorly, but I haven't noticed signs of gradual degradation.  When in its crippled state, the computer seems "alive" but stifled.  Symptoms:

-- Applications are nearly impossible to launch.  For instance, if launching an application from a panel button, the "exploding box" will take 1-2 minutes to draw, gradually expanding in 15-20 second intervals.  Firefox will take about 2 minutes to launch and is basically unusable when it does launch.

-- Pings from other computers respond as normal.

-- SSH server does not respond.  I am unable to log in from other computers, but normally this works fast and reliably.

-- Samba server does respond, but not quickly enough to maintain good throughput.  I can browse and read/write small files, but media is out of the question.  (My iTunes Library for my Macs lives on this computer, and when the Ubuntu box is in this state they can't maintain a good enough connection to the server.  The remote Macs' Finder and/or iTunes will hang waiting for the server to respond.)

-- System seems "capable" of running at full speed for brief moments, yet as though something is throttling it back most of the time.  For instance, hitting the log out/switch user button in the top corner will (after a minute or so) bring up the correct dialog.  When it does do so, clicking "cancel" seems to allow the system to run full-speed for 15-20 secs or so, but it will eventually slow to a crawl again.

I'm no "noob," but this honestly has me stumped.  I've examined system logs (which don't seem to reveal anything untoward), shut down unnecessary services, disabled my AGP-connected Nvidia graphics card (the system is now running with on-board video), and still the problem eventually occurs.  I don't precisely know when or how the problem manifests itself, since this is mostly a file server computer and I only notice the slowdown after it's already happened.  A forced power-cycle restart always restores full functionality.  (I don't like the power-cycle restart, but when in this state, the computer is unable to shut itself down properly.  It gets to the Ubuntu splash screen and hangs.)

This seems like a classic memory leak, but I have no hard evidence to prove this.  I added GDesklet processor and memory monitors today to perhaps see what's going on.  I'll also be leaving top running to look for problem children.  

For the record, this also happened in 6.10 Edgy.

Can anyone point me in a good direction to start troubleshooting?

Cheers,
adam

---

