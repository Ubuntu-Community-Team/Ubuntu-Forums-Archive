---
title: "Booting Errors after update to 4.15.0-43"
date: 2019-01-07
forum: General Help
---

### Post by oxilite on 2019-01-07
Hey all, so I'm generally pretty comfortable with Ubuntu, but i get a little iffy when it comes to kernel level and boot issues, so apologies if I don't explain this exactly right.

Had  strange issue pop up last night when I updated Ubuntu 18.04 and rebooted.  The machine which had obviously been running, no longer booted.  instead I got errors about ACPI Exception (which I think might already have been there), but it was followed by:

ata3: softreset failed device not ready
ALERT! UUID=[Partition UUID] does not exist Dropping to a shell!

at which point i was dropped into Busy Box.  I'll admit I'm running on some pretty janky hardware, but I was able to confirm in BB and Grub that the UUID did in fact match what was output from blkid.

Attempted to boot back into 4.15.0-42 and 4.15.0-43 recovery mode, but neither would get any further.

Strangest of all, the fix action seemed to be to unplug a second hard drive that was plugged in, but not being used.  This hadn't been a problem before (as evidenced by the fact that it was plugged in already, and up and running), and Grub was clearly booting off the correct hard drive, and BB was identifying the right UUID on the correct hard drive, so I really cant account for why the update would cause the boot to fail, and why simply unplugging a second drive would bring it back to life.  I still get the ACPI Exception errors, but they don't even appear over the splash screen, so I don't know that I care, but just curious since I couldn't find any information on any of the above.  Let me know if any other logs or info would help.

---

### Post by oldfred on 2019-01-08
Did you image copy a partition to drive that you unplugged? That may have created a duplicate UUID?
Not sure what else might cause issue. 

In old days when device /dev/sda1 was used instead of UUID or labels, plugging in a drive may change drive order and that would cause issues.

D

---

### Post by oxilite on 2019-01-08
Hmm, at one point I had tried to use that drive as part of a RAID, but never in conjunction with the drive that was ultimately booting Ubuntu. And I thought about drive order, except that I hadn't added that drive recently, so not sure why it would have changed, plus I got to GRUB.  Thanks for the suggestion though, someday I'll have to re-look at the bad drive.

---

