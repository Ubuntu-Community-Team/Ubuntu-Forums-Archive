---
title: "Delay some processes"
date: 2018-05-12
forum: General Help
---

### Post by raleigh3 on 2018-05-12
andyk_~/Downloads$ systemd-analyze blame
         13.967s [email]udev-configure-printer@-devices-pci0000:00-0000:00:13.2-usb2-2\x2d4.servic[/email]e
         11.173s NetworkManager-wait-online.service

Is there a way to have these processes start after bootup in order to speed up my boot up time?

---

### Post by Autodave on 2018-05-12
My machine boots up in less time than either of those processes do. What are the specs on that machine? What is your total boot time?

---

### Post by raleigh3 on 2018-05-13
Startup finished in 5.237s (kernel) + 41.907s (userspace) = 47.145s

processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 21
model        : 48
model name    : AMD A8-7600 Radeon R7, 10 Compute Cores 4C+6G
stepping    : 1
microcode    : 0x6003106
cpu MHz        : 1396.282
cache size    : 2048 KB

1 Tb hard drive. 8 Gb ram.

---

### Post by HermanAB on 2018-05-13
You can disable the processes completely:
systemctl stop [servicename]
systemctl disable [servicename]

and then let your desktop system start them with a batch file.  

Put a Desktop Entry file (with .desktop extension) inside of ~/.config/autostart (for one user) or /etc/xdg/autostart for all users.

---

### Post by raleigh3 on 2018-05-13
Does this look o.k.?

#!/bin/bash
# Ubuntu_Mate 16.04 LTS
#
#
start apt-daily.service
start [email]udev-configure-printer@-devices-pci0000:00-0000:00:13.2-usb2-2\x2d4.servic[/email]e

And should they show when I run systemd-analyze blame?

---

