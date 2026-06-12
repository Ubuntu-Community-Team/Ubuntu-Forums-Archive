---
title: "NTFS incredibly slow and consuming all of (Q6600) CPU!"
date: 2013-12-23
forum: General Help
---

### Post by guisar on 2013-12-23
I'm running 13.10 and have an external USB drive and an internal windows 7 partition (dual boot).  The mount.ntfs process is consuming 99% of CPU according to top- the whole machine is obviously incredibly slow.  Trying to access anything on the NTFS partitions is painful.  No other issues with the machine.  These are the only NTFS remnants I have left- so don't have another machine to test on or see if this is an issue with other machines.  Machine is operating with SATA internal drives and the USB external is a 2.0 port and drive.  

I have found a lot of older references to an out of control NTFS process but dont' see a ton of posts here.  Is this a known (suck it up) issue or is there a solution/set of problems which cause? It's debilitating as I have to keep the external drive as NTFS.

Here is HW /driver info:
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
        Subsystem: Gigabyte Technology Co., Ltd Device 5004
        Kernel driver in use: uhci_hcd
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
        Subsystem: Gigabyte Technology Co., Ltd Device 5004
        Kernel driver in use: uhci_hcd
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
        Subsystem: Gigabyte Technology Co., Ltd Device 5004
        Kernel driver in use: uhci_hcd
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
        Subsystem: Gigabyte Technology Co., Ltd Device 5006
        Kernel driver in use: ehci-pci

 and a hdparm reading (presuming it's useful)
/dev/sdc:
 Timing buffered disk reads:  82 MB in  3.02 seconds =  27.11 MB/sec
vice the (also seemingly very slow internal drive)
/dev/sdb:
 Timing buffered disk reads: 248 MB in  3.00 seconds =  82.58 MB/sec

---

### Post by electrohandyman501 on 2013-12-23
Are you booting/running the OS completely from the external drive?

---

