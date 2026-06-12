---
title: "Can't power down external drive"
date: 2014-01-11
forum: General Help
---

### Post by nstgc379 on 2014-01-11
I've tried to power it down two ways. The first way is with the Disks utility, and the other was in terminal with udisks --detach.

In case of the former, with the GUI, it starts powering down but then remounts everything.

In the case of the later, in terminal, after using "sudo udisks --unmount /dev/sdXY", where X is the device and Y is the partition, I use "sudo udisks --detach /dev/sdX" but get the error message:

Detach failed: Error detaching: helper exited with exit code 1: Detaching device /dev/sdX
USB device: /sys/devices/pci0000:00/0000:00:1c.0/0000:06:00.0/usb4/4-1/4-1.4)
SYNCHRONIZE CACHE: FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: FAILED: No such file or directory

I really don't like turning the thing off without spinning down the drive, but thats what I've been doing.

---

### Post by tgalati4 on 2014-01-11
Install *acpitool* and examine the power status of your usb ports:

```
apcitool -w
```

Also check your BIOS for usb settings such as "Allow USB device to wake" and turn that off.

---

### Post by nstgc379 on 2014-01-11
When I run "acpiitool -w" in terminal I get:
```

   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. BR20	  S3	*disabled  pci:0000:00:1e.0
  2. USBE	  S4	*enabled   pci:0000:00:1a.0
  3. NPE1	  S4	*disabled  pci:0000:00:01.0
  4. NPE2	  S4	*disabled  pci:0000:00:01.1
  5. NPE3	  S4	*disabled  pci:0000:00:02.0
  6. NPE4	  S4	*disabled
  7. NPE5	  S4	*disabled
  8. NPE6	  S4	*disabled
  9. NPE7	  S4	*disabled  pci:0000:00:03.0
  10. NPE8	  S4	*disabled
  11. NPE9	  S4	*disabled
  12. NPEA	  S4	*disabled
  13. PEX0	  S4	*disabled  pci:0000:00:1c.0
  14. PEX1	  S4	*disabled  pci:0000:00:1c.1
  15. PEX2	  S4	*disabled  pci:0000:00:1c.2
  16. PEX3	  S4	*disabled
  17. PEX4	  S4	*disabled  pci:0000:00:1c.4
  18. PEX5	  S4	*disabled
  19. PEX6	  S4	*disabled
  20. PEX7	  S4	*disabled  pci:0000:00:1c.7
  21. GBE	  S4	*enabled   pci:0000:00:19.0
  22. EUSB	  S4	*enabled   pci:0000:00:1d.0

```

I haven't looked into my BIOS settings yet, as I'm currently trying to get a bunch of stuff done before the new semester starts (including putting my class together :S, something that I should have already done). I can check that out later today though.

---

### Post by nstgc379 on 2014-01-11
Bump. I don't have any relavent BIOS settings.

---

