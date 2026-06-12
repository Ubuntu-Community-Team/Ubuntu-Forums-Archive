---
title: "Ubuntu does not start up after a crash"
date: 2007-08-06
forum: General Help
---

### Post by SleepJunkie on 2007-08-06
I'm running the latest version of ubuntu. I've had this installed for a month or two I guess and everything has been running perfectly. I started having a problem with my connection, so I went into those settings. I'm not sure exactly what happened after that, but the computer froze. I left it alone for a while, but nothing happened. I couldn't safely shutdown, so I pulled the plug.

Now when I start up, everything seems fine until the login screen. At first it was showing the desktop contents as they were when the crash happened. I restarted again and I'm getting this now. ([http://i12.tinypic.com/4kk68f7.jpg](http://i12.tinypic.com/4kk68f7.jpg))

I can start up in recovery mode, but I'm not sure what to do from there. If I attempt to start up in 2.6.20-15 I get to the loading screen and the status bar doesn't move.

Any ideas? Thanks.

---

### Post by AlexThomson_NZ on 2007-08-06
Broken xorg.conf?  Does dmesg or Xorg.0.log give any clues?

---

### Post by SleepJunkie on 2007-08-07
I'm really not sure what I should be looking for. When I run dmesg it's filled with things saying it can't turn a cooling device on. Is there anything specifiic I should be looking for?

---

