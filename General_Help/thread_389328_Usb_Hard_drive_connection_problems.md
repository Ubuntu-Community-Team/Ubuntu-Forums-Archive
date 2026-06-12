---
title: "Usb Hard drive connection problems?"
date: 2007-03-20
forum: General Help
---

### Post by Lupurus on 2007-03-20
Hello, I just got Ubuntu recently and am having some USB hard drive problems.
My drive is a Samtack 320GB external hard drive. So, my computer doesn't seem to recognize it all the time. As in, when I boot up or plug it in or turn it on, sometimes computer won't see it at all, and sometimes it is recognized for a few seconds, then Ububtu chastises me for disconnecting my USB drive unsafely.
When I type "tail -n 20 /var/log/syslog" into the terminal just after activating the drive, (I dunno what it means, someone just told me to try that), it says:

Mar 20 13:23:33 Lupurus kernel: [17187567.820000] usb 2-3: new high speed USB device using ehci_hcd and address 85
Mar 20 13:23:34 Lupurus kernel: [17187568.692000] hub 2-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
Mar 20 13:23:34 Lupurus kernel: [17187568.804000] usb 2-3: new high speed USB device using ehci_hcd and address 86
Mar 20 13:23:35 Lupurus kernel: [17187569.676000] hub 2-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
Mar 20 13:23:35 Lupurus kernel: [17187569.788000] usb 2-3: new high speed USB device using ehci_hcd and address 87
Mar 20 13:23:35 Lupurus kernel: [17187570.196000] usb 2-3: device not accepting address 87, error -71
Mar 20 13:23:35 Lupurus kernel: [17187570.308000] usb 2-3: new high speed USB device using ehci_hcd and address 88
Mar 20 13:23:36 Lupurus kernel: [17187570.716000] usb 2-3: device not accepting address 88, error -71

The USB cable is definitely not bad, because it works on other computers.
Any ideas?
-Lupurus

---

### Post by chewearn on 2007-03-21
Maybe it's contact between the particular USB cable and connector on your PC.

---

### Post by Lupurus on 2007-03-21
Perhaps. Do you think switching up the usb cable would help, or do I have to mess around with my computer's guts?

---

### Post by chewearn on 2007-03-21
Not sure if you have multiple usb ports, and have tried them all?  Also, is the PC getting old (usb port wearing out)?  You can try switching cables, maybe it will work (it didn't work for me last time, see below).


Just want to share about my previous experience:
My old departed PC :-({|= was heavily used for many years; during its final years, the front usb ports started to cause hard lock-up when doing large data transfer.  Changing cables doesn't help.  Later, I was planning to swap out the usb connectors; a tedious task, not easy to find replacement parts, plus soldering required.  But before I got around to it, the PC decided to call it a day, and went dead.:cry:

---

### Post by Lupurus on 2007-03-23
Aww! that's terrible!
I have 4 USB ports, none of which yield preferable results... However, they do respond to other usb devices. Based on all that I'd tend to believe it was a software problem, except that the same problems happened in windows. Sooo... My friend has a new... um... usb receptor thingy, so I could replace the ports if I wanted to...
But that doesn't make a whole lot of sense.
Thanks for you help though! :)

---

### Post by Lupurus on 2007-03-24
Different things happen different times...  here are some more logs:

Mar 24 12:27:55 Lupurus kernel: [17189116.268000] usb 4-1: new high speed USB device using ehci_hcd and address 41
Mar 24 12:27:56 Lupurus kernel: [17189116.676000] usb 4-1: device not accepting address 41, error -71
Mar 24 12:27:56 Lupurus kernel: [17189116.788000] usb 4-1: new high speed USB device using ehci_hcd and address 42
Mar 24 12:27:56 Lupurus kernel: [17189116.808000] usb 4-1: device descriptor read/8, error -71
Mar 24 12:27:56 Lupurus kernel: [17189116.928000] usb 4-1: device descriptor read/8, error -71


And


Mar 24 12:29:53 Lupurus kernel: [17189233.496000] usb 4-1: new high speed USB device using ehci_hcd and address 45
Mar 24 12:29:53 Lupurus kernel: [17189234.016000] usb 4-1: device not accepting address 45, error -71
Mar 24 12:29:53 Lupurus kernel: [17189234.128000] usb 4-1: new high speed USB device using ehci_hcd and address 46
Mar 24 12:29:54 Lupurus kernel: [17189234.648000] usb 4-1: device not accepting address 46, error -71
Mar 24 12:29:54 Lupurus kernel: [17189234.760000] usb 4-1: new high speed USB device using ehci_hcd and address 47
Mar 24 12:29:54 Lupurus kernel: [17189235.168000] usb 4-1: device not accepting address 47, error -71
Mar 24 12:29:54 Lupurus kernel: [17189235.280000] usb 4-1: new high speed USB device using ehci_hcd and address 48
Mar 24 12:29:55 Lupurus kernel: [17189235.688000] usb 4-1: device not accepting address 48, error -71

---

### Post by Lupurus on 2007-03-26
bump

---

### Post by taseedorf on 2008-01-09
I think the problem you're getting is in regards to a known bug which won't let Ubuntu mount a drive (usb) that has been improperly unmounted on windows.  Do you always use "safely remove hardware"??  Anyways, I believe you can fix it by setting it up on windows, hitting safely remove hardware, than turning the drive off if possible, and than unplugging.  Than try it in Ubuntu and it should work, let me know if it did.

---

