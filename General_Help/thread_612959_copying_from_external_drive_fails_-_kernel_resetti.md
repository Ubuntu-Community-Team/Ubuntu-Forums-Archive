---
title: "copying from external drive fails - kernel resetting device"
date: 2007-11-14
forum: General Help
---

### Post by ddonaldd on 2007-11-14
Feisty Fawn on a P4-1.8 Mhz, 1 GB RAM
Linux ben 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux

Problem: copying files from USB external hard drive (40 GB Maxtor 3.5") fails.  The drive is mounted successfully, but when I start copying from it, the copying speed slows down and eventually stalls.

/var/log/messages is filled with these:
ov 14 12:53:45 ben kernel: [  499.024000] usb 4-1.3: reset high speed USB device using ehci_hcd and address 4

The drive and cabling are fine.  Copying is fast and reliable when the external drive is plugged into a Windows XP machine.

This is from /var/log/messages after connecting the drive:

Nov 14 12:50:49 ben kernel: [  322.996000] Initializing USB Mass Storage driver...
Nov 14 12:50:49 ben kernel: [  322.996000] scsi0 : SCSI emulation for USB Mass Storage devices
Nov 14 12:50:49 ben kernel: [  323.000000] usbcore: registered new interface driver usb-storage
Nov 14 12:50:49 ben kernel: [  323.000000] USB Mass Storage support registered.
Nov 14 12:50:54 ben kernel: [  328.000000] scsi 0:0:0:0: Direct-Access     MAXTOR 6 L040J2           0000 PQ: 0 ANSI: 0
Nov 14 12:50:54 ben kernel: [  328.036000] SCSI device sda: 66055248 512-byte hdwr sectors (33820 MB)
Nov 14 12:50:54 ben kernel: [  328.040000] sda: Write Protect is off
Nov 14 12:50:54 ben kernel: [  328.044000] SCSI device sda: 66055248 512-byte hdwr sectors (33820 MB)
Nov 14 12:50:54 ben kernel: [  328.044000] sda: Write Protect is off
Nov 14 12:50:54 ben kernel: [  328.044000]  sda: sda1
Nov 14 12:50:54 ben kernel: [  328.052000] sd 0:0:0:0: Attached scsi disk sda
Nov 14 12:50:54 ben kernel: [  328.068000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 14 12:52:52 ben kernel: [  446.096000] usb 4-1.3: reset high speed USB device using ehci_hcd and address 4
Nov 14 12:52:53 ben kernel: [  447.204000] usb 4-1.3: reset high speed USB device using ehci_hcd and address 4
Nov 14 12:52:54 ben kernel: [  448.280000] usb 4-1.3: reset high speed USB device using ehci_hcd and address 4
Nov 14 12:52:55 ben kernel: [  449.356000] usb 4-1.3: reset high speed USB device using ehci_hcd and address 4
Nov 14 12:52:56 ben kernel: [  450.432000] usb 4-1.3: reset high speed USB device using ehci_hcd and address 4
Nov 14 12:52:57 ben kernel: [  451.524000] usb 4-1.3: reset high speed USB device using ehci_hcd and address 4
Nov 14 12:52:58 ben kernel: [  452.600000] usb 4-1.3: reset high speed USB device using ehci_hcd and address 4
Nov 14 12:52:59 ben kernel: [  453.676000] usb 4-1.3: reset high speed USB device using ehci_hcd and address 4
Nov 14 12:53:01 ben kernel: [  454.748000] usb 4-1.3: reset high speed USB device using ehci_hcd and address 4

---

### Post by ddonaldd on 2007-11-15
any suggestions?

---

### Post by ddonaldd on 2007-11-16
bump

---

### Post by HAARP on 2008-01-14
I'm having the same problem (different distro tho). What kernel is Feisty using? Did you manage to get rid of it?

[My thread summing it up](http://www.linuxquestions.org/questions/linux-hardware-18/random-read-hangs-with-usb-hdd-613491/)
[A thread on Ubuntu forums with a possible solution](http://ubuntuforums.org/showthread.php?t=163716)
[another thread on a different forum proposing solutions](http://forums.fedoraforum.org/showthread.php?t=103776)

All these solutions did not work for me.

---

### Post by ddonaldd on 2008-01-14
I spent a lot of time researching this, no help from Ubuntu Forums though.  Only thing I managed to find is that it is a kernel issue.  Never found a fix however.

---

### Post by HAARP on 2008-01-14
Solved it.
After adding a third stick of RAM, the mem as a whole was running out of spec. I had to downclock it from 320 MHz to 306 MHz. Now it's running stable without any problems reading from that disk

---

