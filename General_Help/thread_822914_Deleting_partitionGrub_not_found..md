---
title: "Deleting partition/Grub not found."
date: 2008-06-08
forum: General Help
---

### Post by LoadedBum on 2008-06-08
I deleted the partition with Ubuntu on it and reconnected the unallocated space with my C drive again. Now when I try to turn my PC on, it says GRUB not found or something like that. Any tips?

---

### Post by unutbu on 2008-06-08
Go to [http://www.users.bigpond.net.au/hermanzone/p18.htm#Keep_GRUB_and_Make_a_Dedicated_GRUB](http://www.users.bigpond.net.au/hermanzone/p18.htm#Keep_GRUB_and_Make_a_Dedicated_GRUB)
Click on "Windows XP 'Recovery Console' method" if you have XP, or read the other links to find the best solution for you.

---

### Post by Rocket2DMn on 2008-06-08
If you are using windows XP, boot into the Windows CD and enter the recovery console.  From there, run
```
fixmbr
```
If you are using Vista, see here - [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392) - you will want /fixmbr and /fixboot.

---

### Post by Oldsoldier2003 on 2008-06-08
the super grub cd can restore your windows mbr.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by LoadedBum on 2008-06-08
More problems.

I do not have a floppy drive.
I'm using the disc to run Linux.
I don't have anything to use a a USB thing.

How would I go about getting this to work?

---

### Post by Rocket2DMn on 2008-06-08
The Super GRUB Disk is burned to a cd-r.  Otherwise, you just need your Windows XP install disc.  No floppy or USB device is necessary to restore Windows to the MBR (and thus eliminating GRUB).

---

