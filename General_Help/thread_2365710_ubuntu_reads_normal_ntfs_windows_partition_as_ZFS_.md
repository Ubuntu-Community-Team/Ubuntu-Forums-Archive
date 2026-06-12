---
title: "ubuntu reads normal ntfs windows partition as ZFS Device. Cannot mount."
date: 2017-07-09
forum: General Help
---

### Post by link626 on 2017-07-09
I have a 2nd hard drive that was used with Windows.
It has 2 ntfs partitions.
linux can see the first partition, and read its contents.

The second partition is also ntfs, but linux sees it as ZFS Device, unknown filesystem type 'zfs_member'

and won't let me mount it.

As far as I can tell, it should be exactly like the first ntfs partition.

How do I mount the second partition that it incorrectly sees as a "zfs" device?

---

### Post by link626 on 2017-07-09
I had to delete and reformat that big partition ntfs with gparted in order for linux to see it.

The drive as it existed under Windows was unreadable, and zpool said it was corrupted. But Windows reads all the files on that partition just fine, with no errors on checkdisk.

I wish someone knew a way to fix it without losing all the data, or needing to recover the files.

---

### Post by Autodave on 2017-07-10
No expert here on Windows (and I don't want to be either), but I believe that you cannot mount it because it was never properly dismounted in Windows. With "fast boot" enabled in Win, the drive is not released when Win is shut down. Not sure that you could do anything about getting it to read now. Hopefully someone else will have better info for you.

---

### Post by Mark Phelps on 2017-07-10
@Autodave is right -- recent Windows versions (i.e., Win8 & Win10) enable Fast Startup by default, and this is a new Hibernation option that keeps the Windows filesystems mounted, even when Windows is not running.

You have to turn that off in Windows -- you can not disable it in Linux.

There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.
 
Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup
 
Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F
 
In both cases, reboot Windows.
 
NOW, FastStartup is disabled.

---

