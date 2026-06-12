---
title: "Failure to initialize HAL after installing ATI binary drivers (6.10)"
date: 2007-02-15
forum: General Help
---

### Post by bhtooefr on 2007-02-15
System specs: ThinkPad R51e, Celeron M 360J, 768MB RAM, Radeon Xpress 200M chipset/IGP

I just installed 6.10 a couple of days ago, and noticed that game performance was dreadful, so I assumed that 3D rendering support wasn't installed. So, I installed the ATI binary drivers as per a document on the Ubuntu wiki.

Afterwards, when I rebooted, I got the "Internal error" "failure to initialize HAL" error. Otherwise, the system worked fine (except I noticed that my NTFS partition was not named by volume name on the desktop, but rather device name), but I wanted that error to go away.

I found out that reinstalling HAL in Synaptic should fix it, so I did so. It wanted to reboot, but I didn't feel like letting it, because I already had some stuff running that I didn't want to close.

After a while, I noticed that I had no sound, so I decided to reboot. When I did so, the HAL error came back. :mad: Sound was working, though.

Does anyone have any suggestions?

**Edit:** Seems like the problem went away on its own...

---

