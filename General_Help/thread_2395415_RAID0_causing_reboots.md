---
title: "RAID0 causing reboots"
date: 2018-07-02
forum: General Help
---

### Post by demigh0d1 on 2018-07-02
Discovered my server crashed this morning. Nothing in the logs to indicate why. 

Array was showing inactive so I stopped and re-assembled it.

After a few minutes of rebuilding the volume, the system suddenly reboots and then is stuck in a boot loop. I have to pull the second drive to get it to fully boot. I've done this several times with the same result.

No errors shown on the console. No errors written to the logs (not on the array volume). I redirected ALL syslog output to an ssh session. No errors there either.

As long as I don't add the second drive it's fine.

Any suggestions on how to proceed would be appreciated.

Duane




4.14.37-129 #1 SMP PREEMPT Sun Apr 29 12:24:05 UTC 2018 armv7l armv7l armv7l GNU/Linux
DISTRIB_DESCRIPTION="Ubuntu 16.04.4 LTS"

---

### Post by TheFu on 2018-07-02
swap out the 2nd drive?

---

### Post by demigh0d1 on 2018-07-02
> **TheFu said:**
> swap out the 2nd drive?

That's my plan at the moment. I've ordered a replacement.

Still, it would be nice to know why it's causing the reboot/boot loop.

---

### Post by TheFu on 2018-07-02
Did you check the SMART data for the drive?
Have you tried swapping the data and power cables?

RAID0 is dangerous, BTW.

---

### Post by demigh0d1 on 2018-07-02
> **TheFu said:**
> Did you check the SMART data for the drive?
Have you tried swapping the data and power cables?

RAID0 is dangerous, BTW.

The drives don't support SMART.[INDENT]

=== START OF INFORMATION SECTION ===
Vendor:               WD
Product:              My Passport 25E1
Revision:             1021
Compliance:           SPC-4
User Capacity:        1,000,170,586,112 bytes [1.00 TB]
Logical block size:   512 bytes
LU is resource provisioned, LBPRZ=0
Rotation Rate:        5400 rpm
Serial number:        WX21AC77PPTP
Device type:          disk
Local Time is:        Mon Jul  2 11:44:54 2018 PDT
SMART support is:     Unavailable - device lacks SMART capability.
[/INDENT]

Swapping cables makes no difference.

With only two USB 3.0 ports I'm pretty much limited to RAID0 on this board (ODroid-XU4). I have the OS on SD card, the external drives are for application data.

---

### Post by TheFu on 2018-07-02
If it is USB3, plug it into another device and check the SMART data from that machine instead.  SMART must be enabled in the BIOS to work. If SMART doesn't work, that is an odroid problem, not WDs.

Linux has lots of different RAID levels supported that aren't connected to what a motherboard supports.  mdadm is how to control that, but really RAID0 should only be used if you are willing to lose all the data on  all the drives in the RAID set.  I only use RAID0 on temporary video "work areas" that nothing is left on more than about 12 hours.  Purely used for performance. Usually, it is much safer to use SSDs to get more performance than RAID0.

BTW, showing the exact command run w/ options + inputs and using "code tags" so things line up is very helpful.

---

### Post by demigh0d1 on 2018-07-02
My mistake, this one is actually a RAID1 mirror, not RAID0.

---

### Post by demigh0d1 on 2018-07-03
I did get smarctl working once I figured out the correct device type. 

No errors reported. Both short and extended offline tests completed without error.

---

### Post by TheFu on 2018-07-04
> **demigh0d1 said:**
> I did get smarctl working once I figured out the correct device type. 

No errors reported. Both short and extended offline tests completed without error.

Can you prove this statement by posting the SMART results?

---

