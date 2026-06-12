---
title: "Booting Ubuntu from external hard drive"
date: 2015-08-21
forum: General Help
---

### Post by john446 on 2015-08-21
I have read my older threads about trying to resolve this and none of them worked...so here I am.

I installed Ubuntu on my external hard drive, partitioned off a section of the HD for itself. While in Windows, I can't see the partitioned part of the HD and I can't assign a letter drive to it in Disk Management, don't know if that has anything to do with it or not.

 I also did this on a different computer than what I am trying to boot it on now. 

In my bios settings I did change the boot order to have the external at the top, after saving and rebooting, the computer will just say "loading operating system" for about 3-4 minutes. After this time, it will just load Windows (normal windows boot on my PC doesn't take that long).

Is there something I missed on installation?

---

### Post by ajgreeny on 2015-08-21
What do you mean by:-
"I installed Ubuntu on my external hard drive, partitioned off a section of the HD for itself."

Did you have more than one partition on the disk when you installed ubuntu or did you partition of the section afterwards?
Did you choose "Something Else" when you installed Ubuntu and where did you install grub? By default grub will be installed on the first hard disk, which in your case will mean the internal disk not the external one.  That may be the cause of your problem, but I would have expected that to simply not boot anything, Ubuntu or Windows.

Forget about seeing the partition from Windows; Linux filesystem partitions are seen by disk-management as partitions but they can not be read or used by Windows and will not appear in the file-manager unless you install a third party driver for ext partitions.

See Boot-Repair in my signature and follow the instruction in that to run the boot-info script in a live ubuntu system, then post back here the link to the report it will create.

---

### Post by yancek on 2015-08-21
> I also did this on a different computer than what I am trying to boot it on now. 


Can you clarify that, please.  The way I read it, you had this external drive attached to another computer, not the one you aree now using when you did the install.  Is that correct?  If so, did you change the default for "Device for bootloader installation"?  You would have needed to do that as the default is to install to the first hard drive which is almost always going to be an internal drive.  Generally it would be /dev/sdb, /dev/sdc depending upon the number of drives attached. 

>  I can't see the partitioned part of the HD and I can't assign a letter  drive to it in Disk Management, don't know if that has anything to do  with it or not.

That would be pointless as explained by ajgreeny above and has nothing to do with your problem.  Best bet to get help is posting the output of the CreateBootInfo summary suggested.

---

### Post by efflandt on 2015-08-22
Did the external drive boot on the computer you used to install Ubuntu to that drive, and does that computer still boot when the external drive is NOT connected?

Even if both computers use BIOS (not UEFI) sometimes even if you change boot order in BIOS, the system will not automatically boot from a removable drive unless that was the last thing it booted (at least Dell in particular, maybe to avoid accidentally booting something unknown or potentially dangerous). The only virus I ever caught (in Windows) was a boot sector virus spread by accidentally booting an infected floppy disk long ago. So you may still need to press a hotkey during the BIOS splash screen to select the external drive even if you have that set higher in boot priority.

It could get more complicated if the computer used to install to the external drive used BIOS and the one you are trying to boot is a newer one that uses UEFI and secure boot (typically if it came with Win8 or newer). But I am not familiar with that yet because even my Win8.1 PC at work uses BIOS and msdos partitions, so it had no trouble booting a regular live/install iso on USB.

---

