---
title: "Need help to confirm possible Gnome bug"
date: 2007-01-06
forum: General Help
---

### Post by dcstar on 2007-01-06
In my 6.10 system I have noticed that if I go into System-Preferences-Sessions and un-tick the "**Show splash screen on login**", then on the next reboot the gnome-volume-manager is not started and my USB stick is not auto-mounted (it is detected in dmesg, but not mounted).

I can manually start the gnome-volume-manager and all is well after that, but it is supposed to start up when Gnome starts!!

I have done multiple reboots on my system with this ticked and un-ticked, and the results are consistent (ticked: everything ok, un-ticked: problems!).

Can some other people try this on their systems and report back if anything untoward happens?

I also notice that my hddtemp package also does not start up when this is un-ticked (I'm not sure what else isn't working.....)

---

### Post by orb9220 on 2007-01-07
All I have to test is my usb sansa player and it shows up when splash is on or off.

after logging out and logging back in.

---

### Post by dcstar on 2007-01-07
> **orb9220 said:**
> All I have to test is my usb sansa player and it shows up when splash is on or off.

after logging out and logging back in.

It's not a login/logout issue for me, it's when I reboot that I have the issue when Splash is off.

---

### Post by dcstar on 2007-01-07
> **dcstar said:**
> In my 6.10 system I have noticed that if I go into System-Preferences-Sessions and un-tick the "**Show splash screen on login**", then on the next reboot the gnome-volume-manager is not started and my USB stick is not auto-mounted (it is detected in dmesg, but not mounted).

I can manually start the gnome-volume-manager and all is well after that, but it is supposed to start up when Gnome starts!!

I have done multiple reboots on my system with this ticked and un-ticked, and the results are consistent (ticked: everything ok, un-ticked: problems!).
.......

I have just checked this on another 6.10 system (with far less packages installed than my home one), and the problem does not occur.

It looks like I have a package/option installed that changes something in Gnome to cause this issue when I disable the Splash screen option - I don't like my chances of finding it as I have quite a few packages installed on top of the basic Ubuntu install........       :(

---

