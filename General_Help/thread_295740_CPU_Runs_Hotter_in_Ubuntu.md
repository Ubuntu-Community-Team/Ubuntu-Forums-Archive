---
title: "CPU Runs Hotter in Ubuntu"
date: 2006-11-08
forum: General Help
---

### Post by Synikk on 2006-11-08
I've notice that my CPU idles at about 39 degrees celcius in Ubuntu, compared to the 37 degrees which it idles at in Windows XP.

Any idea why it would run warmer in Ubuntu?

---

### Post by lowracer on 2006-11-08
Ubuntu uses a brown theme, which is considered a warmer color than Windows' default of blue. This warmth causes the effect you're seeing. :D 

Seriously, run the 'top' command and see what is actually running when you think Ubuntu is idling.  You might have something like a beagle daemon running that is using up significant percentage of CPU time when otherwise it seems like the system isn't being used.

---

### Post by fragos on 2006-11-09
This could be a calibration issue.  Sensors don't read directly in degrees.  A numeric value is read normalized and converted with a mathmatical expression.  Windows and Linux may have a slightly different conversion variables.  Linux allows you set low value, high value, multiplier and offset.  This is not to say CPU utilization might be a factor.

---

