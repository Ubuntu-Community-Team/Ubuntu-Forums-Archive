---
title: "Gnome 3.6.2, random short lockups + no brightness controls with Nvidia driver"
date: 2013-03-24
forum: General Help
---

### Post by Roasted on 2013-03-24
I'm running Ubuntu 12.10 with Gnome 3.6.2 on several machines. Netbook, laptop, desktop, and a Macbook Pro. I'm experiencing some issues on the Macbook Pro, but I'm not sure if the MBP is to blame or the driver or what. It all started with seeing that my system would lock up every so 20-30 seconds, but only for 3-4 seconds at a time. It never fully locked up and would continue fine, but like I said it happened frequently so it was a continual bother. I disabled all extensions and also noticed that with no programs running it continued, so that kind of ruled out any programs or extensions being the issue for the lockup. I tried the Nvidia 304 drivers, 310, etc., but all were the same. I also noticed with the actual Nvidia drivers, I lost my brightness controls. It seems as if the lagging is gone with them, though... I don't recall seeing it, but the brightness was also pegged at 100% with no controls to lower it so I didn't use it for too long since it was burning my retinas, so I guess there's still room for the random lagging persisting.

The GPU in the MBP is an Nvidia 9400. I'm wondering if the 9400 itself is problematic with the Nvidia drivers (even multiple versions) or if there is a different level of complexity with the fact it's running on a Macbook Pro. What would be interesting if anybody running Gnome 3.6.2 with an Nvidia 9400 could comment that would help determine if it's the Apple gear or if there's a regular issue with the drivers on that GPU right now. 

Secondly, even if I install the official Nvidia drivers, is there a way to re-acquire the brightness controls? Currently if I raise or lower the brightness it does absolutely nothing, meanwhile the brightness is stuck at 100%. 

Any insight would be appreciated!

EDIT - I think my experience was somewhat tainted by a deeper issue with the Macbook Pro. I booted back to OSX and 5 times in a row had kernel panics. OSX doesn't just panic 5 times in a row. Even Windows ME doesn't act that bad. I let it go for a day but the next morning I flat out couldn't boot into OSX. I figured this was due to me mucking around with the partition table and partition layout. I ended up doing a fresh OSX 10.8 install and a fresh 12.10 install and left it alone. After that things seemed to operate fine without the random hangups.

---

