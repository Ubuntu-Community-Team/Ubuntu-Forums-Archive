---
title: "Can't get an edit of system files to stick - overwritten on reboot"
date: 2014-04-28
forum: General Help
---

### Post by garethfoxwilliams on 2014-04-28
To overcome an external USB sound issue, I need to make my CPU run at a faster, ideally constant speed.

I've followed the steps of this page:
[http://superuser.com/questions/454101/](http://superuser.com/questions/454101/)

My edits seem successful but disappear after a reboot.

I've tried the variation of doing it all as root ( sudo su) and also trying chmod -w to prevent the files being written over, but they are overwritten to their original values during a reboot.

Basically, I want to alter the cpu frequency scaling from *ondemand* to *performance* and to keep this permanent.

The files are in 
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

and

/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor


Any ideas, please?

---

