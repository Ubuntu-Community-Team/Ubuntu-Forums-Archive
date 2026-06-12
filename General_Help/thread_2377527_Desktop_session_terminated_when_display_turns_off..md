---
title: "Desktop session terminated when display turns off.  CEC commands were the culprit"
date: 2017-11-14
forum: General Help
---

### Post by james5mith on 2017-11-14
I just reinstalled my system from 17.04 to 17.10 (reformat and clean install.)

Everything seems great, except for when my screen (A 40" cheapo LG 4K TV) is powered off, my entire desktop session is terminated.  I've never before experienced this with Ubuntu or any other OS.

I can't seem to find anything when searching the forums, but maybe I'm using the wrong search terms?

I also don't see anything obvious in the syslog as to what might be causing this.  Is it because it's an HDMI display? [B]CEC is disabled if that helps.  <-- Update:  Nope!
[/B]
If I lock my session, then unlock it, everything is fine.  But if my screen goes into power saving, or if I actively power it off/on, the desktop session is destroyed.

I would even be happy just to hear that it isn't just me this is happening to.

This is happening in both the standard Ubuntu Desktop environment, and the Ubuntu Desktop on Xorg environment.



**Edit:  Turns out that bold part was not true.   CEC (Or as LG calls it Simplink) was in fact, _**still on**_.  And apparently the Ubuntu Desktop now honors CEC commands, so when the display powers off, it sends the CEC command for the desktop to power off, which terminates the user session.  (Does not actually turn off the systemthough.)*
*After disabling CEC, my initial tests show that the desktop session is no longer terminated when the display powers off.*

---

