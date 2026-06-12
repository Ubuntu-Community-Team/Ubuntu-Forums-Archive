---
title: "Ubuntu not &quot;seeing&quot; my wireless or bluetooth adaptors"
date: 2016-06-20
forum: General Help
---

### Post by Evil Wayz on 2016-06-20
I have not changed anything, or added any programs.  The only thing I did was unplug a ten slot usb adapter to plug my backup drive into the usb directly on the box, because it doesn't play nice with the hub.  Now, bluetooth doesn't work, and neither does my wireless N adapter.  When I start blueman it tells me there is no bluetooth adapter present. 

I have another hard drive plugged into the box directly and it shows up on lsusb:
```
wolf@shaitan:~$ lsusb
Bus 001 Device 009: ID 1058:0748 Western Digital Technologies, Inc. My Passport (WDBKXH, WDBY8L)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

and this command yields nothing:

```
wolf@shaitan:~$ dmesg | grep -i bluetooth
wolf@shaitan:~$ 

```

I have had problems with bluetooth and wi fi connecting before, but it has always detected my dongles.

I am using xubuntu desktop in Ubuntu16.04, witht eh generic 4.4 kernel.

---

