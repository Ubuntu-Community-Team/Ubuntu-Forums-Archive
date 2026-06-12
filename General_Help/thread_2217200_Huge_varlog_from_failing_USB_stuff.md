---
title: "Huge /var/log from failing USB stuff"
date: 2014-04-16
forum: General Help
---

### Post by o-s-diab on 2014-04-16
I'm running Xubuntu 14.04. Everything is working great, but I'm getting huge log files that are eating up my entire partition!

Here' s what tail of syslog says:

```
Apr 15 23:23:14 puppytron kernel: [ 9387.275222] usb 1-1: Not enough bandwidth for altsetting 1
Apr 15 23:23:14 puppytron kernel: [ 9387.275223] 2:3:1: usb_set_interface failed (-22)
Apr 15 23:23:14 puppytron kernel: [ 9387.275242] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8804082bc640
Apr 15 23:23:14 puppytron kernel: [ 9387.275243] xhci_hcd 0000:00:14.0: Trying to add endpoint 0x82 without dropping it.
Apr 15 23:23:14 puppytron kernel: [ 9387.275244] usb 1-1: Not enough bandwidth for altsetting 1
Apr 15 23:23:14 puppytron kernel: [ 9387.275244] 2:3:1: usb_set_interface failed (-22)
Apr 15 23:23:14 puppytron kernel: [ 9387.275306] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8804082bc640
Apr 15 23:23:14 puppytron kernel: [ 9387.275307] xhci_hcd 0000:00:14.0: Trying to add endpoint 0x82 without dropping it.
Apr 15 23:23:14 puppytron kernel: [ 9387.275308] usb 1-1: Not enough bandwidth for altsetting 1

```
What can I do with this?

---

### Post by mikewhatever on 2014-04-16
What do you mean by "failing USB stuff "?  ...possibly in non-vague terms.

---

### Post by o-s-diab on 2014-04-17
I don't know, I just am reading from the logs. Nothing apparently fails, I just get huge logs about it as in the original post. Its filled up my hard drive completely already (can't even write a vim swap file)

---

### Post by tgalati4 on 2014-04-17
Open a terminal and post the output of:

```
lsusb
```

Remove all USB devices and see if the logs quiet down.  Could be a failing motherboard.

---

### Post by o-s-diab on 2014-04-17
Bus 002 Device 004: ID 2109:0812  
Bus 002 Device 003: ID 2109:0812  
Bus 002 Device 002: ID 2109:0812  
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 009: ID 17cc:baff Native Instruments Traktor Kontrol S4
Bus 001 Device 017: ID 058f:9410 Alcor Micro Corp. Keyboard
Bus 001 Device 013: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 012: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 018: ID 2687:fb01  
Bus 001 Device 016: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 015: ID 04f9:0272 Brother Industries, Ltd 
Bus 001 Device 014: ID 09e8:006b AKAI  Professional M.I. Corp. 
Bus 001 Device 011: ID 2109:2812  
Bus 001 Device 010: ID 0d8c:0319 C-Media Electronics, Inc. 
Bus 001 Device 008: ID 2109:2812  
Bus 001 Device 007: ID 2109:2812  
Bus 001 Device 002: ID 045e:075d Microsoft Corp. LifeCam Cinema
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I'll see if any particular usb device looks feisty.

---

### Post by tgalati4 on 2014-04-17
It could be one of your 4-port hubs that has failed.  Try to get to a minimum configuration and see if your system acts normally.  Then plug each device in one-hour intervals and check your *dmesg*:

```
dmesg | tail -40
```

When your messages go crazy, unplug the last device and do some research on it.  Perhaps others are having problems with it.

---

