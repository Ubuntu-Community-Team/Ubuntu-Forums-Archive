---
title: "Kapcid and Kapcid notify woes"
date: 2008-04-30
forum: General Help
---

### Post by jjgy on 2008-04-30
A quick background:  I had Gutsy running on this same machine, but switched from ubuntu after installing an 8800GT graphics card.  (I never could get x to work with it.)  I just now installed Hardy Heron.

The install was ridiculously slow, and the moment I could I checked my processes from a terminal.  I noticed that kapcid and kapcid_notify (pids 45 and 46 respectively) were hogging 99% cpu total.  I went ahead and reniced the processes while I finished up my install, and then took a look at the processes.  A quick google search turned up similar issues to mine, and I suppose it's my Celeron D processor which causes this issue.  (Please note the problem did not exist on my gutsy install, so it could be the 8800.)  Anyway, for whatever reason, apci does not want to work without causing that infinite loop, so I added apci=off to my kernel line in /boot/grub/menu.lst.  That fixed the cpu problem, but left me without internet access.  Any attempts to connect left me with a failure while trying to obtain an ip address.

I've seen several other people with this problem, but so far, it appears disabling acpi (a big deal on a laptop, not on a desktop however) is the only fix.  Unfortunately, this seems to break internet connection for some people.  Any ideas?

---

