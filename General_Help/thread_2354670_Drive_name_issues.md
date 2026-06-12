---
title: "Drive name issues"
date: 2017-03-05
forum: General Help
---

### Post by natesnape on 2017-03-05
I'm having a bit of an issue with one of my NTFS drives, this happened after I cleaned my PC and disconnected my external drives, it seems that my External Drive now has a different name when mounted, attached is[ATTACH=CONFIG]273995[/ATTACH] a screenshot of my issue. 
As you can see the drive name is *Wanderer *while the mounted name is *Wanderer1. *All help is much appreciated.
Thanks in advance.

---

### Post by vanadium on 2017-03-05
Unmount and remove the drive, then delete the mount point (folder) /media/natesnape/Wanderer that likely will exist under /media/natesnape. Next time you mount the drive, it probably will be mounted correctly again.

---

### Post by natesnape on 2017-03-05
> **vanadium said:**
> Unmount and remove the drive, then delete the mount point (folder) /media/natesnape/Wanderer that likely will exist under /media/natesnape. Next time you mount the drive, it probably will be mounted correctly again. 

That solved my issue! However I had to run PCpacman in Root mode. Another issue came up where I can't empty my Trash because the Wanderer folder was there, I manually removed it via the thrash-empty command, but I got this error "Segmentation fault (core dumped)" after emptying the trash. Hopefully everything works fine tomorrow, Will post another topic if another issue comes up, many thanks mate!

---

