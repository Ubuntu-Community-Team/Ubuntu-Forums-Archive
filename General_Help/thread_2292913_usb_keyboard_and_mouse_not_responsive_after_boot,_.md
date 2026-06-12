---
title: "usb keyboard and mouse not responsive after boot, work ok after reboot"
date: 2015-09-01
forum: General Help
---

### Post by migurus on 2015-09-01
Ubuntu 14.04 Desktop installed on Dell XPS 8700 desktop with Windows 7 as dual boot. 
```
~ uname -a
Linux MYNAME 3.13.0-62-generic #102-Ubuntu SMP Tue Aug 11 14:29:36 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```
I use regular usb keyboard and mouse. 

When system boots up the GRUB screen appears and keyboard works just fine. When Ubuntu login screen is on then keyboard and mouse become dead, plug / unplug does not help. This happens most of the time, only rarely keyboard is OK and I login normally. I tried all different USB ports, but nothing changes.

When keyboard is dead I ssh into the system and reboot it - it always works just fine after that.

Ironically, when I select Windows in GRUB keyboard always works just fine in Windows.

I captured output of lsusb after reboot, when everything works, and after cold boot, when keyboard is dead:

This is when everything OK
```

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0bda:0184 Realtek Semiconductor Corp. RTS5182 Card Reader
Bus 003 Device 003: ID 046d:c069 Logitech, Inc. M500 Laser Mouse
Bus 003 Device 006: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 003 Device 007: ID 13fe:3800 Kingston Technology Company Inc. Rage XT Flash Drive
Bus 003 Device 002: ID 03f0:034a Hewlett-Packard 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

This is when keyboard failed (got it through ssh)
```

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I attached lshw output just in case.

Any help will be appreciated.

---

### Post by VMC on 2015-09-01
Output '*dmesg*'

---

### Post by migurus on 2015-09-03
please see zipped output from dmesg attached

---

### Post by VMC on 2015-09-03
```
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 14 ports detected

hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected

hub 1-1:1.0: USB hub found
hub 1-1:1.0: 6 ports detected

usb 3-13: USB disconnect, device number 6

Chicony HP Elite USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input5

Chicony HP Elite USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.1/input/input6

Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input7
```

You have a HP keyboard and a Logitech mouse, but what are those hubs? Also it appears you disconnected the keyboard at one point.

---

### Post by migurus on 2015-09-05
I do not have any USB hubs, don't know what are those hubs in the report.
The unplug message was from me unplugging USB flash drive

---

### Post by VMC on 2015-09-05
Sometimes, usb keyboards appear as hubs, and some actually are with other ports on them. 

Have your tried un-plugging the mouse and see if the keyboard works by itself. Just to eliminate conflicts.

---

### Post by migurus on 2015-09-05
Yes, I did try un-plug and plug into other usb jacks, but it did not make any difference.

---

### Post by s72 on 2015-09-16
I am experiencing a very similar problem on my ACER laptop.

The built-in keyboard and touchpad always work but external (USB-) keyboard and mouse work just fine at the GRUB screen but usually go dead at the login screen.

The problem was introduced after a kernel upgrade to version 3.13.0-**62**-generic (i.e. the same kernel-version that you have).

With kernel 3.13.0-**62**-generic I was usually able to resolve the situation with a reboot but things got worse after upgrading to the next kernel-version (3.13.0-**63**-generic) and it now takes two or three reboots before things work alright.

I have now figured out that I can work around the problem by selecting the "Advanced ..." boot option at the GRUB screen and have the system boot with an older kernel-version. - It is perhaps only a coincident but for the past couple of days I have worked around the problem successfully by choosing to boot with kernel-version 3.13.0-**61**-generic.

---

### Post by migurus on 2015-09-19
Not much luck with this problem.
People, what would be other forums to ask for help?
Recommendations appreciated

---

