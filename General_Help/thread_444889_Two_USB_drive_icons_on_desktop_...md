---
title: "Two USB drive icons on desktop .."
date: 2007-05-15
forum: General Help
---

### Post by ss0007 on 2007-05-15
Hi thr ,
When I recently booted Ubuntu fiesty with my attached USB CD-ROM and USB pen drive . There are two icons appeared on the desktop for the same drive . e.g
One is pointing to -> /media/KINGSTON
Second one is pointing to ->  /media/KINGSTON_

[[IMG]http://img444.imageshack.us/img444/4071/drivesoj0.th.jpg[/IMG]](http://img444.imageshack.us/my.php?image=drivesoj0.jpg)

It looks to be bug in Ubuntu fiesty fawn, Is there anyway to lock it down.I mean , can 
I use any log files to report it in launchpad. Since , they may need to know the exact situation.

Can someone help me ?

---

### Post by laidback on 2007-05-15
Have you got 2 partitions on your USB drive?

---

### Post by x64Jimbo on 2007-05-15
> **laidback said:**
> Have you got 2 partitions on your USB drive?
That's my first guess as well.

---

### Post by ss0007 on 2007-05-16
Nope ...just one partition in the drive ... 
The duplicate entries just came when I booted .Seems to be a rare situation to occur .

Anyway , there 's one more thread to confirm this .. 
[http://ubuntuforums.org/showthread.php?t=442009&highlight=duplicate+drive+icons+desktop](http://ubuntuforums.org/showthread.php?t=442009&highlight=duplicate+drive+icons+desktop)

Any ideas ... ??

---

### Post by laidback on 2007-05-17
This is a long shot. Have you by any chance got the selection pins at the back of your USB hdd set to cable select. Apparently Linux prefers Master or Slave. On my USB drive I have it set on Master.

---

### Post by x64Jimbo on 2007-05-20
> **laidback said:**
> This is a long shot. Have you by any chance got the selection pins at the back of your USB hdd set to cable select. Apparently Linux prefers Master or Slave. On my USB drive I have it set on Master.
It's a pen drive. There is no master or slave setting.
Anyway, it sounds like a bug. You may want to check the bugtracker.

---

### Post by nowshining on 2007-07-31
have the same thing, a workaround is to right click the icon, select unmount then when all is well and ready, unplug the device, restart the computer, and wait until ubuntu is fully operational and re-plug the device back in, and it shoul not re-occur for awhile - pref. a week or so..or something unexpected happens...

edit: Note log in first to and wait to see the desktop before re-plugging it back in..

---

### Post by fela on 2008-03-27
i have the same problem, with my kingston datatraveler 2GB pen drive. :confused: i hope this bug is fixed in hardy

---

