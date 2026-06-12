---
title: "Clock can't keep time"
date: 2008-02-03
forum: General Help
---

### Post by Mostlyharmless42 on 2008-02-03
My clock seems to be 30 mins fast per day.  It's messing up my alarms. I reset my clock 2 days ago, and no it's an hour ahead again.  When i set it to automatic, it won't reset.

---

### Post by erfahren on 2008-02-03
is it set correctly in the BIOS?

here's a few threads about clock/time problems that may help
[http://ubuntuforums.org/showthread.php?t=219340](http://ubuntuforums.org/showthread.php?t=219340)
[http://ubuntuforums.org/showthread.php?t=509252](http://ubuntuforums.org/showthread.php?t=509252)
[http://ubuntuforums.org/showthread.php?t=129536](http://ubuntuforums.org/showthread.php?t=129536)

---

### Post by accatagon on 2008-02-03
The clock is based on your hardware, so I don't think there's much you can do software-wise to make it work properly. One possible workaround is to keep it synchronized with a time server. Right click on th time, click preferences, and click Adjust Date & Time, and change the configuration to "Keep Synchronized with internet servers." If it asks you to install NTP, do so, and select which time-servers to use. I'm not sure how often the software synchronizes, but if it's often enough, it should work properly. 

Otherwise, you could get a new motherboard or somehow replace the system clock. . .

---

