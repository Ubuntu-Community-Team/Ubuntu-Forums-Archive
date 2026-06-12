---
title: "No display when booting after 12.10 upgrade"
date: 2012-10-27
forum: General Help
---

### Post by camper365 on 2012-10-27
I am running Ubuntu Studio 12.10 on a Dell Latitude D630 after a "do-release-upgrade" from 12.04.  The upgrade ran without problems, but when I rebooted, grub loaded and ran, but then there was a black screen (the display was off).  There was disk activity, so I let it run for a little bit, and eventually the login prompt came up, so I logged in and everything was fine.  The next morning I tried to dock my laptop, and the same thing happened, only after the login prompt both displays were off.  The computer was still running, so I went to a virtual terminal, and the displays were still off, but I hit Ctrl+Alt+Del and saw a pixelated version of my default desktop.  It was unusable since I had just told the computer to reboot, but it was the first image I had seen since login.  When shutting down with the computer undocked Plymouth works properly during the shutdown process.  When docked the displays remain off.
Has anybody else had this problem, and if so, how did you fix it?

---

### Post by camper365 on 2012-10-27
I also found that I can dock it while it's already booted and running, run ArandR, and both displays will work.

---

