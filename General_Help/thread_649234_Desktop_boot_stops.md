---
title: "Desktop boot stops"
date: 2007-12-24
forum: General Help
---

### Post by Martyhartwell on 2007-12-24
HI

I upgraded from 7.04 to 7.10 about 2 weeks ago, I think it worked all right for a few days. Then I was notified of automatic updates. Now when I boot it does the splash screen, the orange bar is advancing to the right. At some point it goes to a black screen with boot messages on and stops at:
 Fatal Error: Failed at /lib/modules/2.6.22-14-generic/kernel/acpi/battery.ko no such file or directory.
I can enter esc followed by an enter and get it to go on up and seems to work. However sometimes the wireless network doesn't come up and I have to manually get it to work. I have looked into this some and I appears as though it is trying to check the status of a laptop battery. Since it is a desktop and doesn't have one it is no surprise it can't find one. My question is have I somehow set something during my poking around, 
Related questions are: is there a place for boot logs? I have found some of the logs of the system in /var/log but I don't see a boot log to follow the boot sequence, That may help me fine the problem. I also had an issue with the sound card not working after the upgrade but I found that it was muted and have put a sleep in its launch with allows it to come up okay now. 
Thanks Marty

---

