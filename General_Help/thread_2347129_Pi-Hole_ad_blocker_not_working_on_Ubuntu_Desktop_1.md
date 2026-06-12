---
title: "Pi-Hole ad blocker not working on Ubuntu Desktop 16.04 after rebooting"
date: 2016-12-21
forum: General Help
---

### Post by mgarrett682 on 2016-12-21
I ran the Pi-Hole ad blocker on a Raspberry Pi running Raspbian for nearly a month with no problem. I decided to install it on a desktop running Ubuntu Desktop 16.04 and shut down the Pi. The installation process ran just as it had on the Pi and after making the changes to my router to route DNS requests to the desktop it worked fine until I rebooted the desktop. When I rebooted the desktop the Pi-Hole wasn't working. I would have to re-enable it from a terminal window (either pihole restart or service dnsmasq restart) in order for it to work rather than it automatically starting every time the machine booted. The folks at Pi-Hole Userspace suggested a number of fixes, none of which worked.

A debug log showed that the Pi-Hole was configured to use the network interface eno1 but that eno1 didn't exist, which is strange because the ethernet adapter in the desktop was using eno1 at the time the debug was run. We tried using crontab with a @reboot line to enable it but that didn't work either.

Any Ubuntu users running Pi-Hole? Or does anyone have any idea why Pi-Hole might not be picking up the eno1 at boot time?

---

