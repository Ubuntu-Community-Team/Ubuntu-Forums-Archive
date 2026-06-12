---
title: "I cannot figure out how to get what follows to a develper"
date: 2016-11-01
forum: General Help
---

### Post by mikeincousa on 2016-11-01
Please help me get to the following to right folks.

I have an apparently obscure issue with 16.04 Desktop. 

[I]It may be a bug or it may be rooted in my ignorance?
[/I]
Namely 

Ubuntu 16.04 is not identifying a older USB drive, which may have been formatted to NTFS under Vista or a Ubuntu version from the same era.

Ubuntu readily mounts a flash drive NTFS formatted in 16.04 for testing purposes.

Windows 10 readily mounts the older drive and the flash drive.

The flash drive appears in the Ubuntu basic utilities. The older drive does not.

Forum posts here and in the Craigslist Linux forum have not produced a hint of a solution.

Here is the Craigslist forum header-shortened from the subject line of my posts in the Ubuntu forum:
 [B]
"Ubuntu 16.04 Desktop, Two NTFS USB drives"

[/B]This tread provides the only, unsuccessful, attempts at a solution.

If you need any more information let me know.

Your help will be appreciated.

Thank you.

---

### Post by TheFu on 2016-11-01
Some USB devices just don't work with some USB ports.  I usually see this with booting issues, but the drive can be read post-boot almost always.

Some usb devices simply aren't recognized. Sometimes it is the cable or the port used.  Sometimes it is the drive controller.  Very hard to tell.  I'd start with lsusb to see if the reported device is a known problem (use google with the device number).

Did you check the log files?  Anything interesting/related in those?

Also, just because a device works with Windows, that doesn't mean it will work with Linux.  Contact the vendor and ask for Linux drivers.  If it is out of support (and when it comes to Linux, they generally refuse support anyway), not much can be done besides asking for help on reputable forums and taking the device to your local LUG for those guys to figure out.

Another option is to remove the HDD from the enclosure and directly connect it to a computer - usually via SATA. A little more effort, but often only 2-4 screws and really easy.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)  The only trick is finding the correct upstream project.

Assuming my ignorance has almost always been the correct course. Of the 500 "bugs" I thought I found in non-GUI programs/libraries, only 3 were really bugs.
At this point, we don't have enough data to be of any help.

---

