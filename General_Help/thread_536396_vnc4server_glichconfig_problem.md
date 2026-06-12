---
title: "vnc4server glich/config problem?"
date: 2007-08-27
forum: General Help
---

### Post by EnthropyinAction on 2007-08-27
I used <a href="http://ubuntuforums.org/showthread.php?t=122402" target="_blank">this</a> HOWTO to set up a VNC server on my home machine, and all seems to be working fine.

The other night, I was logged into it from work and noticed a definate slow down.  We currently have a bandwidth graph setup for our office (recent move, we're using a 3 T-1 lines instead of fiber temporarily and have to be mildly conservative) and when I looked at it, I alone was using almost 4mbps.  I closed everything, but the graph didn't drop until I killed the (idle) VNC session.  

First of all, my connection at home is limited to 2mbps so I'm not sure how it was using that much.  I restarted the client and started with the lowest quality settings, working my way up to full color (too laggy to use, but just a test) and the graph never went above 200kbps.

I hadn't seen the problem before this and I'm really not sure what caused it.  Could it be something in my server's config settings or mebbe client?  When the client first connects it tells me there's no encryption so could someone have broken into the connection and sucked the bandwidth for no reason?  I'm just a bit confused and want to try to understand what's going on.  

I can post config files up if anyone wants em; maybe I made a typo?

---

