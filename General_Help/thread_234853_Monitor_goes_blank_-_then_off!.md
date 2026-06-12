---
title: "Monitor goes blank - then off!"
date: 2006-08-12
forum: General Help
---

### Post by homersbrain on 2006-08-12
I have a problem, which appears to be random, in that the monitor will suddenly blank (goes black) and then go into standby. Only a reboot brings it back up. There is no problem with the hardware because it never ever happens in windows. I reinstalled dapper again to see if XGL screwed something, but it's still the same. Sometimes I can run ubuntu for an hour, other times less than 10 mins. My vid card is a radeon 9000. Is problem in the ati driver, X or even the kernel?

---

### Post by Perfect Storm on 2006-08-12
Perhaps the monitor is singing on the last note.

---

### Post by wpshooter on 2006-08-12
Have you tried another monitor to eliminate that as a possible problem.

Do you have monitor/display standby/power management parameters turned off in BIOS ?

Have you edited xorg.conf file and changed from ATI to fglrx ?  This may or may not be problem.  You might want to do some research on this.

I assume you have all of the available updates for Ubuntu installed.

I had some problems with monitor blanking on a random basis and it was solved by setting the screensaver and power management functions in the proper order.

---

### Post by CypherHackz on 2008-01-09
i also have the same problem. i dont think it is because of the monitor because my  monitor is new. just bought it one month ago. it does not happen in windows. only in ubuntu.

---

