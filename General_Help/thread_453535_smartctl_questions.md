---
title: "smartctl questions"
date: 2007-05-24
forum: General Help
---

### Post by eleach on 2007-05-24
I have Seagate Barracuda 7200.9 hard disks.

If I do a short test and then do:

   smartctl -l selftest /dev/sda

I get the message:

   Device does not support Self Test logging

When I do:

   smartctl -i -d ata /dev/sda

I get:

   === START OF INFORMATION SECTION ===
   Device Model:     ST3808110AS
   Serial Number:    4LR4EPK1
   Firmware Version: 3.AAH
   User Capacity:    80,026,361,856 bytes
   Device is:        Not in smartctl database [for details use: -P showall]
   ATA Version is:   7
   ATA Standard is:  Exact ATA specification draft version not indicated
   Local Time is:    Thu May 24 13:06:52 2007 CDT
   SMART support is: Available - device has SMART capability.
   SMART support is: Enabled

Is there any way I can get logging to work?

Also, in smartd.conf, I have the line:

   /dev/sda -H -d ata -m <myemailaddress>

I don't have a mail server on my computer, so will it really email me if it finds something wrong? If not, how can I get it to alert me?

Thanks

---

