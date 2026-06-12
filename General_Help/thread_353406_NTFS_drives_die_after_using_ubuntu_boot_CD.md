---
title: "NTFS drives die after using ubuntu boot CD"
date: 2007-02-04
forum: General Help
---

### Post by kel-chan on 2007-02-04
I originally downloaded ubuntu to make a boot CD from it in case my Windows XP should ever die (since floppy drives are getting hard to find these days). In any case, the boot CD worked fine after trying it on 2 different computers.

Once trying the ubuntu, the main computer was rebooted and worked fine. It then crashed a day later on some weird exception (blue screen of death, would have to consult husband on actual message since I didn't see it but it was not standard). At the time, we thought this was caused by a failed fan on the video card. However, we have tried swapping, re-seating and cleaning all cards and not chkdsk comes up with bad errors on our NTFS drives for anything recent (2 physical drives, one 9GB, one 34GB, 3 logical on the 34GB, including windows) and goes into a reboot loop. We also tried hooking these drives into the computer that does work (these are SCSI drives, so it's easy) but with Windows XP, the computer will go into reboot loop and with ubuntu, the drives are visible but not accessible.  Ubuntu also still boots on the original big computer but no dice on accessing the drives there either.

Is it possible that the ubuntu CD messed with the registry in some way? Or initialized it in a way that is incompatible with Windows XP? I did a search for this topic but the closest that I cam up with was titled "system crash" and the guy ended up buying a new computer. Suggestions? Commiserations?

Thanks,
kel-chan

---

### Post by kwaanens on 2007-02-04
Ubuntu does not mount ntfs-partitions as read/write by default (some tweaking is needed for that), so my guess would be: this has nothing to do with it.
If you made ubuntu write to ntfs-partitions: that might very well be the reason, officially you shouldn't do that.

---

### Post by dcstar on 2007-02-04
> **kel-chan said:**
> 
.........
Is it possible that the ubuntu CD messed with the registry in some way? Or initialized it in a way that is incompatible with Windows XP? I did a search for this topic but the closest that I cam up with was titled "system crash" and the guy ended up buying a new computer. Suggestions? Commiserations?

Thanks,
kel-chan

The only thing - apart from a hardware fault - is that the XP system now sees the drive layouts differently due to the Ubuntu install.

How did you install Ubuntu?, was it on unused space on the first or second drives?

Post your /boot/grub/menu.lst file contents here.

---

