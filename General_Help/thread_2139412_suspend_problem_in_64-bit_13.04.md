---
title: "suspend problem in 64-bit 13.04"
date: 2013-04-26
forum: General Help
---

### Post by entropy1 on 2013-04-26
(Ubuntu not Lubuntu) When try to suspend, my laptop immediately wakes up if I have an external keyboard/mouse connected to the usb port.  If I disconnect and then suspend, the laptop stays suspended.  The methods suggested in [http://ubuntuforums.org/showthread.php?t=1444822]("http://ubuntuforums.org/showthread.php?t=1444822") posts 5 and/or (7 & 19) have not worked for 13.04.  If there are more up-to-date suggestions, I'd like to know.

---

### Post by entropy1 on 2013-04-27
Bump...

---

### Post by kamranm1200 on 2013-04-27
Probably has something to do with your laptop's configuration or the way you have Ubuntu setup.

---

### Post by cprofitt on 2013-04-27
What is the model and make of your laptop?
Do you know what video card is in use?

---

### Post by entropy1 on 2013-04-27
Here is the basic information:

```
HP EliteBook 2740p

Intel(R) Core(TM) i5 CPU M 540 @ 2.53 GHz 2.53 GHz
4.00 GB (3.80 usable)
64-bit OS
Pen & Touch Input Available with 2 Touch Points

Intel(R) 82577LM Gigabit Network Connection
Intel(R) Centrino(R) Advanced-N 6200 AGN
```
```
$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5050(size=8)
```

---

### Post by entropy1 on 2013-05-26
Bump.  I've tried the standard ubuntu desktop install, ubuntu gnome install, and a minimal install, and the problem continues...

---

