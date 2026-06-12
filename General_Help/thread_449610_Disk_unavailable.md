---
title: "Disk unavailable"
date: 2007-05-20
forum: General Help
---

### Post by jhenrik on 2007-05-20
History:  Installed Ubuntu into an existing WinXP Home system.  The system uses an Abit KT-7A Raid motherboard.  Raid was not activated, allowing two additional IDE channels.  Thus a total of four IDE channels for a possible eight devices.  Under XP, IDE channel 1 Master was a DVD-RW, IDE channel 2 Master a CD-RW.  The Slaves 1 and 2 were unused.  IDE channels 3 & 4 are controlled by the built in HPT 370 raid controller bios.  Hard drives (total of four) were attached to the Master and Slave of each channel.  IDE 3 Master was the WinXP boot disk.  This configuration ran well for a number of years.

To install Ubuntu, a hard disk (IDE 3 Slave) was cleaned off and made the Master.  Ubuntu installed without problems, but the system would not boot.  Several attempts were made and several bios combinations tried, but could not get beyond the computer reboot loop.  The Grub screen never appeared.  The IDE 3 install did not work.

Changing disks to IDE 1 (Ubuntu Master and WinXP Slave) solved the problem.  Grub edit provided full dual boot capability.  Ubuntu installation, fully updated and upgraded to 7.04, runs fine.  Configuration is now:  IDE 1 Master Ubuntu, Slave WinXP; IDE 2 Master DVD-RW, Slave empty;  IDE 3 Master and Slave, both WinXP Fat 32 disks; IDE 4 Master CD-RW, Slave empty.  

Casualty:  WinXP recognizes all devices but the IDE 4 master CD-RW.  Highpoint site indicates their Raid controller bios recognizes only formatted hard drives.  Would like to copy from one CD to the other without caching, but can live without it.

Current Issues:  

Ubuntu recognizes all disks in device manager, but the browser does not show the IDE 3 Master disk.  How do I make this disk available?  

The contents of the IDE 3 Slave are available to Ubuntu.  The name was changed from the XP name.  Would like to keep consistent names.  Is this changs normal?

Is there a way to make the system bootable with Ubuntu installed on the IDE 3 Master disk?

Thanks

---

### Post by mbradlcu on 2007-05-21
oh man,, yep I had this issue.. here's a link to what was the fix for my kt7a-raid and it's a pretty good read about grub.
[http://lists.gnu.org/archive/html/bug-grub/2004-07/msg00113.html](http://lists.gnu.org/archive/html/bug-grub/2004-07/msg00113.html)

---

### Post by jhenrik on 2007-05-23
Hi

Many, many thanks for the reply.  It exactly describes the problem.  Implementing the fix is way beyond my capability.  My consolation is that I didn't overlook any of the resources I had.  I will leave the configuration as is for now and post another thread directed at the unlisted drive.

Again, many many thanks.

Jerry

---

