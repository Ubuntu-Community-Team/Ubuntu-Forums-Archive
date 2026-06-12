---
title: "Ubuntu 15.04 &amp; Teamviewer - Stop Job taking 1m30sec"
date: 2015-04-05
forum: General Help
---

### Post by george84 on 2015-04-05
Just wondering if anyone has had any experience using Teamviewer under the new 15.04?  I had it installed under 14.04 and it was fine but under 15.04 when I go to shutdown it takes FOREVER now. When I switched back to a console window to see what was going on it is trying to shutdown Teamviewer and states something about stop job running and it counts up to 1m30s before it ends the process. We had a Kingston HyperX SSD in the laptop and it usually boots Ubuntu in about 6 seconds and shuts down in 10.  Any ideas where in the start-up/shutdown scripts I could edit that timeout?

---

### Post by Elfy on 2015-04-05
*Thread moved to **Ubuntu Development Version**.*

---

### Post by Slinkee2k on 2015-08-09
I solved the problem on Ubuntu 15.x, thanks to some other posts:

I posted as "alphacompnet".
[http://teamviewerforums.com/index.php?topic=2495.0](http://teamviewerforums.com/index.php?topic=2495.0)
[https://bbs.archlinux.org/viewtopic.php?id=188990](https://bbs.archlinux.org/viewtopic.php?id=188990)

You have to find your teamviewerd.service file (Teamviewer Daemon config file) and enter ```
TimeoutStopSec = #s
``` where # is the number of seconds for timeout stop.

My file was in ```
./etc/systemd/system/
```

tadaa. (WILL REQUIRE A REBOOT BEFORE TAKING EFFECT. You can stop the Teamviewer daemon from the terminal by typing the following:
```
teamviewer --daemon stop
```

---

### Post by cariboo on 2015-08-09
Moved, this has nothing to do with Wily.

---

