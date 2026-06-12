---
title: "USB mounting issue"
date: 2014-05-07
forum: General Help
---

### Post by fleagleg on 2014-05-07
I'm on Precise ATM and I cannot mount any USB storage. This was working perfectly fine until about a week ago and I hadn't installed any new software at the time. The system recognises the USB device and it shows up in Nautilus. I can right click on the drive and select the mount option but the mount doesn't work. I've tried four different USB storage devicees, two sandisk cruzers, an attache, a PNY, and a SG external hard drive. all of them show "(name of manufacturer) filesystem" but cannot be mounted by any means I know and I haven't found a solution to my problem in my hunting around the web. Any help would be appreciated and anyone who can steer me to a fix earns my gratitude.

---

### Post by squakie on 2014-05-07
Check /var/log/syslog (or the archived .1, .2, etc.) - after the log shows the device (there might be several lines for it), see if there is a warning or error.  I've been having trouble (albeit in 14.04A) with it recognizing but not mounting my camera via USB since early last week - perhaps earlier.  My log show an error bout unable to mount mtd device.  What does your log show?

---

### Post by fleagleg on 2014-05-07
So I found the error you were speaking of, I think
May  6 16:39:33 Sanguis kernel: [77862.145007] Buffer I/O error on device sdb1, logical block 1004770
May  6 16:39:33 Sanguis kernel: [77862.145009] Buffer I/O error on device sdb1, logical block 1004771
May  6 16:39:33 Sanguis kernel: [77862.145010] Buffer I/O error on device sdb1, logical block 1004772
May  6 16:39:33 Sanguis kernel: [77862.145011] Buffer I/O error on device sdb1, logical block 1004773
May  6 16:39:33 Sanguis kernel: [77862.145012] Buffer I/O error on device sdb1, logical block 1004774
May  6 16:39:33 Sanguis kernel: [77862.145013] Buffer I/O error on device sdb1, logical block 1004775
May  6 16:39:33 Sanguis kernel: [77862.145014] Buffer I/O error on device sdb1, logical block 1004776
May  6 16:39:33 Sanguis kernel: [77862.145016] Buffer I/O error on device sdb1, logical block 1004777
May  6 16:39:33 Sanguis kernel: [77862.145017] Buffer I/O error on device sdb1, logical block 1004778
May  6 16:39:33 Sanguis kernel: [77862.145018] Buffer I/O error on device sdb1, logical block 1004779

And it repeats every time I try to mount it

---

### Post by squakie on 2014-05-09
That gives the impression of a bad device.  However, do you have more than 1 disk on your system?  Here is a way to test this better:

- plug in the USB device such as a flash drive
- wait about 30 seconds until the device shows but isn't accessable
- go back to /var/log/syslog and check the messages starting where the USB device is plugged in

---

