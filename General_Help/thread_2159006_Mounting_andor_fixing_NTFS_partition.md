---
title: "Mounting and/or fixing NTFS partition?"
date: 2013-07-01
forum: General Help
---

### Post by jclmusic on 2013-07-01
I am trying to ressurect an old computer running Windows XP. 
I think the hard drive has become corrupted, but I am not sure. I booted up a Xubuntu Live CD to try and rescue any data on the drive before making a dual boot system (or I may just use it as a server). 
Gparted won't let me mount the only partition on the hard drive. It's an NTFS partition and gparted says "Error: NTFS is inconsistent" and to run chkdsk within windows, but that's not possible, because when I try to boot using the hard drive, I get a boot disk failure.

Any ideas?

---

### Post by oldfred on 2013-07-01
You need to boot with your original XP install disk in recovery mode and run chkdsk. I have used a Windows 7 repairCD to run chkdsk on my XP and it worked even better than the XP version, but I also then had to restore the PBR or partition boot sector as the Win7 chkdsk converted it to Win7 type.

The Linux NTFS driver will not normally mount NTFS partitions that are hibernated or have chkdsk flag set to prevent damage that chkdsk may not then fix.

       XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)

---

### Post by jclmusic on 2013-07-01
> **oldfred said:**
> You need to boot with your original XP install disk in recovery mode and run chkdsk. I have used a Windows 7 repairCD to run chkdsk on my XP and it worked even better than the XP version, but I also then had to restore the PBR or partition boot sector as the Win7 chkdsk converted it to Win7 type.

The Linux NTFS driver will not normally mount NTFS partitions that are hibernated or have chkdsk flag set to prevent damage that chkdsk may not then fix.

       XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)

Thanks. Would that result in the loss of the data on the drive, though? I'd like to be able to backup the data there first if at all possible.

---

