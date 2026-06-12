---
title: "Partimage Help"
date: 2007-06-13
forum: General Help
---

### Post by nami on 2007-06-13
i just restored my image file onto a second harddrive as i have 2x 250gb drives.

but something seems strange, everything i do something new on the first drive, it automatically seems to get mirrored onto the second drive.  for example, if i create a textfile on the desktop of drive 1, when i restart and swap drives via the bios, the new textfile appears on the second drive 2?

what's going on?

---

### Post by timzak on 2007-06-13
Just to verify, could you unplug the drive you're not booting up on and see if the file still gets ghosted over?  Perhaps grub is overriding your bios and still booting off of the original drive even though you think you're booting off of the 2nd drive.

---

### Post by nami on 2007-06-13
i will be home in about 2 hours so i will try it then.  thanks for the suggestion.

---

### Post by trippinnik on 2007-06-13
Are you using some kind of software Raid mirroring? I guess the solution of unplugging one of the drives will help figure out what it is...

---

### Post by nami on 2007-06-13
> **timzak said:**
> Just to verify, could you unplug the drive you're not booting up on and see if the file still gets ghosted over?  Perhaps grub is overriding your bios and still booting off of the original drive even though you think you're booting off of the 2nd drive.

that was exactly what was happening... :redface:

---

