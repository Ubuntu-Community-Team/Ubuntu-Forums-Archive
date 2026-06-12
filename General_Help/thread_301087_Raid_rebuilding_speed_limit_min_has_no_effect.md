---
title: "Raid rebuilding: speed_limit_min has no effect"
date: 2006-11-16
forum: General Help
---

### Post by sspade on 2006-11-16
I have created a Raid 5 array with 3 external disks and the rebuild time is approx 5 days!  I've discovered that the speed_limit_min variable is supposed to control the rebuild time, but it doesn't have any effect whatsoever.  I've tried echoing new values into /proc/sys/dev/raid/speed_limit_min, I've tried setting the value with sysctl and I've manually edited the sysctl.conf file, but nothing changes the rebuild speed.  When I type cat /proc/mdstat it still shows the speed_min_limit as 1000K.  

Everything on the web says the change should take place dynamically and immediately; I'd be happy to see any change take place....

Does anybody know what I'm doing wrong?  BTW, I get the same results with both Dapper and Edgy.

rgds
sspade

---

### Post by Amux on 2007-01-04
I've the same problem: [COLOR="DarkRed"]**speed_limit_min has no effect on reconstruction speed**[/COLOR].
My diskparm -Tt doesn't show a particularly slow drive.

I have two Maxtor Diamond Max SATA disks (raid1) on an Asus A8N-E board.

As a minimun I suspect that there is a issue with my motherboard. What's your configuration?

It has been a long time since you posted here. Did you find any solution?

Cheers

---

