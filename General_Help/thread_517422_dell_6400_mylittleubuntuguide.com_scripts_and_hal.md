---
title: "dell 6400 mylittleubuntuguide.com scripts and hal"
date: 2007-08-04
forum: General Help
---

### Post by mattbeau on 2007-08-04
ok Wubi installed Ubuntu on my Dell  6400 without a hitch, there are some scripts that i run in order to get my ati graphics card and wifi drivers to work that were made at mylittleubuntuguide.com after running the scripts and a reboot I get the error "HAL failed to initialize" after I start a new gnome session. I never had any problems running the scripts under a "real" Ubuntu enviroment and am wondering if there is some sort of bug

thanks

---

### Post by tuxcantfly on 2007-08-04
> I never had any problems running the scripts under a "real" Ubuntu enviroment and am wondering if there is some sort of bug

I doubt it could be a Wubi bug; it only differs from Ubuntu in its disk setup, and everything else behaves the same. Scripts like Automatix (which appears to be what the guide's scripts were based off) tinker with the deep internal workings of Ubuntu, and are notorious for breaking working systems; for that exact reason their usage is strongly discouraged, on both standard Ubuntu and Wubi. I believe it's a bug with the scripts (they don't usually work on all hardware, yours was probably incompatible), not with Wubi, but then again, if you ever do make a standard Ubuntu installation on that machine, and it does work, make sure to tell us.

---

