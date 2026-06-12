---
title: "Does usb VOLITILE memory exist?"
date: 2013-12-13
forum: General Help
---

### Post by maestrobwh1 on 2013-12-13
Is there any USB device out there that uses VOLITILE memory?  Odd question, but after searching, I think the answer is no.  I ask here because us Ubuntu'ers are more seemingly more aware of unique things that might exist out there.  All I found was Super Talents DRAM*DISK but that utilizes software (Win only) to create a RAM disk that then syncs to the flash memory from there.  The drive itself isn't DRAM.  

How convenient would it be for something with the speed of "real RAM" to be on USB 3.0 pen drive for swap?    Obviously it would have to be reformatted as swap on each boot, but that isn't anything a script wouldn't handle.  I understand it would still be limited by the USB speed, so 2.0 would only move at 480 MBPS which is still faster than most hard drives.

I have an situation where I have a machine (OQO Model 02) where 1 GB of ram is soldered to the board and I am limited to that.  Ubuntu still works okay with it without swap (it has a PATA SSD, no TRIM) and swap on an external regular flash memory actually seems to bog it down a tad.  Granted, pulling out the drive during operation would be bad without some proper command, and nothing would be saved.

I would also think with an "always on" desktop machine running a VM could take advantage of this, as long as the VM image was actually synced back to the HD.  Imagine how fast a VM machine would run from RAM:-)

---

