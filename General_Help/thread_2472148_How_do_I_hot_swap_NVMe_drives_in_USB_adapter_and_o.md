---
title: "How do I hot swap NVMe drives in USB adapter and old one doesn't display in Disks?"
date: 2022-02-18
forum: General Help
---

### Post by dora5 on 2022-02-18
I'm testing and wiping several hundred NVMe drives by using Disks and a NVMe USB adapter, in Ubuntu.

When I'm done with a NVMe drive, and I take it out of the USB adapter, it still displays in Disks.  See screenshot below after I took the NVMe drive out of the adapter.  


   
If I mount a NEW NVMe drive, teh OLD one STILL displays in Disks.
If I open terminal and type umount /dev/sdb it tells me it isn't mounted, and it still displays it.

I do not WANT to unplug and replug in the USB drive 500 times. I've already worn out two USB drives.

How do I get the blasted drive I took out to no longer display without removing the adapter?

Thanks!

---

### Post by TheFu on 2022-02-18
Forget the GUI. Those are just too slow and too inconsistent.  Don't use **gnome-disks**.

Use **smartclt** for testing.  That means running a test, waiting a few minutes, then running a report. 2 separate commands.  You can easily check the report for concerning values. Never just check the "PASSED" or "GOOD" output.  Those just mean that the test worked.

If you are completely wiping the devices, you'll need to figure out the legal requirements for the wipe. A single wipe isn't considered to be sufficient by any where I've worked. In the govt work, there is a FIPS standard, but I don't think they ever reuse SSD storage, because a wipe really isn't a wipe.  Let's just say that over 50 prior layers of updates have been recovered. There are a number of wipe tools that work at the device level, well below the file systems. Use one of those.  For a home, I'd use at least 3 wipe rounds.  For a medical office, 12 rounds and for something really important, 50 rounds, if I couldn't get approval to just destroy the devices. A "round" is all zeros, all ones, all random, some other pattern, perhaps 00FF, then FF00, and another random. 

If this is really important to your job (you cannot allow any data to leak), talk with a reputable data recovery expert to learn what they can and cannot recover. Don't be surprised and don't leave something this important up to come marketing manager.

If you also plan to lay down standard partitioning and file systems, those can easily be scripted using **sgdisk** and **mkfs**.  

Or if you have to deal with NTFS, **mkntfs** is the command. There are a number of options. 
I haven't thought about this stuff in about a decade.

---

