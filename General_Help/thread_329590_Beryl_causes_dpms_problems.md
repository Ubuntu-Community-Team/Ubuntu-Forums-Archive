---
title: "Beryl causes dpms problems?"
date: 2007-01-01
forum: General Help
---

### Post by glave on 2007-01-01
I'm in edgy kubuntu and a while back discovered the problem many people have had with kde not shutting down their monitor for power save. I got it corrected eventually, though I do not remember what it was I did now.

Fast forward to a few days ago. I've noticed that my monitor no longer turns itself off, the screensaver just displays forever. The ONLY changes my system has been through recently is beryl has updated a few times, and I changed my screensaver from becoming password protected after 90 seconds of being in use.

I've checked my dpms settings using qset, and my values had not changed. I tried setting them to 315 with the screensaver coming on at 300, but the screensaver just kicks in without the monitor powering down 15 seconds later. If I do a **qset dpms force off**, my monitor behaves and shuts right down.

Any possibilities that beryl is somehow hindering dpms abilities? I've told beryl to use kwin instead of itself, but that didn't seem to help either now.

---

