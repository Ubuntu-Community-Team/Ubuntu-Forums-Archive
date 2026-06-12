---
title: "System resumes from suspend immediately..."
date: 2014-04-22
forum: General Help
---

### Post by Roasted on 2014-04-22
Hello friends. I have an Ubuntu 14.04 system running as a HTPC that I just installed. I enabled WOL (wake on LAN) so I can remotely turn the system on via other laptops/tablets/phones via WOL scripts and WOL apps. Thing is, about 50% of the time the system automatically resumes from suspend. I have little doubt that it's centralized around WOL in particular, as the issue didn't come up until then, but I question what I can do to work around it.

I found this post and tried this suggestion from an older Ubuntu release:

[http://ubuntuforums.org/showthread.php?t=1978290](http://ubuntuforums.org/showthread.php?t=1978290)

but I didn't have any luck. The system resumed from suspend that much quicker, and it seemed as if my GUI was unresponsive after resuming. I ended up deleting that script and now everything is back to normal, where it stays suspended about 50% of the time and the other half it auto resumes within seconds of going into suspend.

I checked the BIOS but aside from WOL being enabled/disabled, there aren't really any other power features to toggle.

Any ideas?

---

