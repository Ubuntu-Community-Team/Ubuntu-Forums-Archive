---
title: "How can i run a &quot;fsck -y&quot; automatically at every boot"
date: 2018-11-03
forum: General Help
---

### Post by uefigod on 2018-11-03
I have a old pc that i just use as a mediaserver now, the hard drive might be failing i get that but doing a "fsck -y" manually everytime it asks me to seems to be working fine properly. I live in an area where power outages are pretty common and sometimes the linux pc faces a hard shut down and 3/5 times when i start it again i have to manually move my keyboard and monitor to the second pc and fix it, this is becoming kind of an hassle.

I've looked around for possibilities and many of them seem outdated, this was the one that seemed most plausible - [https://unix.stackexchange.com/a/123964](https://unix.stackexchange.com/a/123964) but sadly i can't find any of the files mentioned in the post ("/etc/init.d/checkfs.sh", "/etc/default/rcS") I'm thinking if the files got moved or fi theres any other way to do it, any help will be highly appreciated, Thanks a ton.

Im on ubuntu 18.04 lts

---

### Post by TheFu on 2018-11-03
Get a UPS that is sized to keep power long enough for a clean shutdown. That can be done manually or using an automatic trigger.  The UPS need to have Linux software for that to work.

I can't help with 18.04, sorry. In 16.04, there was a kernel option to run fsck at boot ; just add it when the grub screen was shown. It was a systemd interface.  Prior to that, just running **sudo touch /forcefsck** was enough to cause the next boot to get a check run. That method has been removed, it seems. 

Google found this: [https://www.freedesktop.org/software/systemd/man/systemd-fsck@.service.html](https://www.freedesktop.org/software/systemd/man/systemd-fsck@.service.html)   but I don't know if it works on 18.04. It might.

---

