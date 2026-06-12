---
title: "[SOLVED] Xorg hangs, logout does not work."
date: 2008-02-26
forum: General Help
---

### Post by mpiktas on 2008-02-26
Some very weird things started going on with my Gutsy installation. At start I can login and work with no problems, but when I want to log out, the system just hangs. Only the power button works. I've created another user, the problem persists. After reboot  I tried shutting down the gdm from the command line without logging in. The script hangs a bit and then ends, but the Xorg is not shut down. It actualy hogs the CPU at 100% and it is not possible to kill the process with kill. I tried various signals with no effect. The only remedy is switching to 1 runlevel and back. 

The curious side effect of this problem is that multimedia keys do not work. With acpi_listen I see that they generate the events, but muting, turning up or down the volume does not work. The same goes for light dimming. I can though switch off the trackpad, so I assume that something is amiss with gnome settings. 

Another thing is that this started one day or two ago, before everything was working normaly. I usually do not turn my computer off, and usually make it sleep. Usually after 2 days of uptime, the multimedia keys started misbehaving, so I just rebooted the computer and everything turned back to normal. 

The Gutsy is installed on Asus F3Jp laptop with ATI X1700 graphics card. I run fglrx driver 8.01 since the one coming with Gutsy did not supports suspending. Gutsy was upgraded from Edgy and Edgy from Feisty.

I would be very thankful for any clues.

---

### Post by imoatama on 2008-02-26
This is a known bug with the 8.01 driver. Upgrading to the 8.02 driver will fix it.

---

### Post by mpiktas on 2008-02-26
So it turns out the two problems were unrelated. 

I upgraded to 8.02 version of fglrx  and logout works again, and the login is much faster. After entering password the Gnome desktop loads almost instantaneously, compared to situation with 8.01 driver, where I had to wait about 20-30 seconds. 

The multimedia keys were not working, since package acpi-support was removed. I removed it accidently when I uninstaled radeontool package. I think it is a bug, acpi-support both suggests and depends on radeontool. Does not make sense for lucky people who are not stuck with ATI. When I reinstalled radeontool and acpi-support the keys started working again.

---

