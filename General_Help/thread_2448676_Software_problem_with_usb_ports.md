---
title: "Software problem with usb ports"
date: 2020-08-11
forum: General Help
---

### Post by marsdenf on 2020-08-11
Using a clean install of xubuntu 20.04 on a fairly new desktop computer.  The comp has two ssd's, one loaded with xubuntu and the other with ubuntu mate 20.04 (clean install).  There are two usb ports on the bottom rear of the pc which are not working in xubuntu but are working on ubuntu mate.  Presumably this means it is a software problem, not hardware.  The ports work with xubuntu when it is in the login screen, but after login and load up, they are broken, sometimes giving neither power nor data and sometimes giving power but no data.  The other usb ports on the back of the comp, and the two on the front, are always working.  When the computer was made for me, I asked for extra usb ports, so maybe the two at the bottom are hardware-separate from the other usb's. Here is the output of lsusb  :

```


 marsdenf@marsdenf-Desktop:~$ lsusb
Bus 009 Device 007: ID 1a2c:2124 China Resource Semico Co., Ltd USB Keyboard
Bus 009 Device 003: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
Bus 009 Device 005: ID b58e:f5a5 Blue Microphones HD Pro Webcam C920
Bus 009 Device 006: ID 04a9:1912 Canon, Inc. HD Pro Webcam C920
Bus 009 Device 004: ID 2109:2813 VIA Labs, Inc. USB2.0 Hub
Bus 009 Device 002: ID 2109:2813 VIA Labs, Inc. USB2.0 Hub
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 003: ID 2109:0813 VIA Labs, Inc. USB3.0 Hub
Bus 010 Device 002: ID 2109:0813 VIA Labs, Inc. USB3.0 Hub
Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 0b05:18f3 ASUSTek Computer, Inc. AURA LED Controller
Bus 005 Device 002: ID 2516:0051 Cooler Master Co., Ltd. AMD SR4 lamplight Control
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
marsdenf@marsdenf-Desktop:~$ 


```

I also tried the live-linux disk which was used for the install, and after trial xubuntu loaded, with the mouse in one of the broken ports, it worked for a second and a half after xubuntu trial loaded, and then the mouse cursor froze.
Which softwares do I have to reinstall to fix this?

---

### Post by kneutron on 2020-08-11
--My advice is not to mess with it.  If Xubuntu is not working with your hardware, the easiest way around it is to install straight Ubuntu and ' apt install xfce4 ' and whatever other packages start with xfce4-.  Otherwise you might find the rabbit hole never ends.

--But if you're determined to chase it down, you could look in 'dmesg' and /var/log/messages for any errors after plugging things into usb under xubuntu, it might be a kernel issue.  And you could make sure all your software is up to date with ' sudo apt update; sudo apt upgrade ' and rebooting.  But I have no idea why you would have 2 separate installs of the same distro level with different desktops when you could Logout and switch to another desktop environment in about 2 clicks...

---

### Post by marsdenf on 2020-08-14
UPDATE:  After checking more carefully, I found that the broken usb ports worked for a few seconds, and then failed on both hard drives (after restarting).  I went into the bios (uefi) and re-enabled fast boot, and that appears to have worked.  Why, I don't know.
UPDATE 2:  Whoops, I spoke too soon.  Problem is now back, on both ssd's.  Oh well.

---

