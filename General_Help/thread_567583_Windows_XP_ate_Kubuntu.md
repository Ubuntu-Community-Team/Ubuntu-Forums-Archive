---
title: "Windows XP ate Kubuntu?"
date: 2007-10-04
forum: General Help
---

### Post by Darby12611 on 2007-10-04
I know, It's Kubuntu, but It's basically the same right? Please help. Alright, I have been running Kubuntu 7.04 for some time, but I'm still pretty much a beginner. I originally wanted to dual-boot with Win XP. But there arose some inconsequential issues, which necessitated the use of a blank HDD for Kubuntu. I put my Win HDD in storage, but I began to miss the larger storage space of the other HDD, and some important files (though I greatly prefer Kubntu). I configured it to be a slave, plugged it in with the secon port on the ribbon cable, and booted. It started trying to boot to Kubuntu, and it said something to the effect of, "Error: hda1 has been mounted 24 times without a check. Check forced." The it said, "Logical error" and then some numerical code(there was the percent of the scan completed listed after the first error messages, but not the proceeding ones. About 14%.). It went on to list (approximately) 30 to 50 other logical errors. It told me to run fsck, which failed. I rebooted, and this time it said, "Error: hda1 contains a file system with errors. Check forced." Then it had all the logical errors with the percent by the first error again. This kept going until I disconnected the Kubuntu drive, configured the XP HDD to be master, and booted from it (Kubuntu HDD still disconnected.). So that's where I am now. Please help!:confused:

---

### Post by Nzer24 on 2007-10-04
Not the most experienced with this type of thing, but it seems that you have a corrupted filesystem. It may or may not be possible to get your data back, but you can try. Run the Kubuntu or Ubuntu (they are the same except for the desktop environment) live CD and try and read the volume and back it up to some other drive. The fact that it booted at all is a good sign. 

Also, why couldn't you put both OSes on the same drive? If you had trouble repartitioning, I can help. Then you could have the second drive available for both systems.

---

### Post by Darby12611 on 2007-10-04
I tried desperately to have both on the same drive. But no matter what I did "Errors occurred while writing the changes to disk" when I tried to partition.

---

