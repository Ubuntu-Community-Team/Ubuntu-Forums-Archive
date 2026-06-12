---
title: "Brother Printer Hangs System Boot Sequence"
date: 2013-06-06
forum: General Help
---

### Post by Ron O on 2013-06-06
I just installed a Brother all-in-one printer MFCJ825DW on Ubuntu 12.04 64 bit by following all the requirements posted on Brother's website, and it seems to work great with one exception. I have to shut the printer completely off before booting my computer or the boot screen hangs at "Auto-detecting USB Mass Storage Devices. Device 01:". This is before the GRUB screen comes up. So I cannot leave the printer on or in sleep mode for receiving faxes, then boot the system without remembering to shut the printer off first and turn it on again after logging in.

I submit this in General because I cannot narrow it down any closer- is it a bios problem (Core 2 Duo generation Desktop computer, AMI bios) or is it a driver problem?  The drivers seem to work fine if you boot, then turn on the printer and use it. I can't find anything on this by searching these forums or Brother's web site.

Short of the right solution (as a workaround), is there a key I can hit to make the system stop looking to configure "Device 01" and have it just resume the boot process?

---

### Post by Ron O on 2013-06-08
Found the solution somewhere else. Looks like it WAS a bios problem. Went into the bios and disabled "legacy" usb detection and left the other USB 2.0 detection settings on high-speed, auto. I'm guessing that the bios could not find a driver for this printer and started searching a long list of legacy devices- perhaps? Boots fine now and all other usb devices including a wireless mouse still work. So I can leave the printer in sleep mode instead of turning it completely off, so it can do it's periodic print-head cleanings. 

Posting my own solution in case someone else runs into the same problem. 

Would like to mark this thread [SOLVED], but that thread tool option still seems to be on vacation.

---

