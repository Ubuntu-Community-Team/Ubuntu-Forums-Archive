---
title: "I have a problem with mounting ntfs partition"
date: 2007-07-06
forum: General Help
---

### Post by ekb on 2007-07-06
I have an external hdd with an ntfs file system. When I plugged it in, the system warns me that it was unable to mount that partition.. now I force mounted it, as a result, the partition came up however, it says WARNING: Dirty Volume mount was forced by the 'force' mount option. Also, I have to do this everytime I want to mount this partition. Does anyone know a solution to this?

thank you!

---

### Post by Mark Phelps on 2007-07-06
Install ntfs-3g.  It will not only handle the ntfs partition better, it will allow for writes as well.

---

### Post by dabl on 2007-07-06
Expanding on what Mark said: [http://kubuntuforums.net/forums/index.php?topic=3084679.0](http://kubuntuforums.net/forums/index.php?topic=3084679.0)

You probably should open that drive in Windows and either reformat or chkdsk it -- it probably got corrupted.  You should not just "pull the plug" on a NTFS-formatted USB drive, because NTFS is a journalling file system. You need to use "eject" or "safely remove" or "umount" or whatever utility is available to tell the system to disconnect from it BEFORE you pull the cable out, so you don't corrupt it.  :)

---

### Post by ekb on 2007-07-06
Sorry to not let you know this earlier, I already installed ntfs-3g on my computer. The problem probably was that my partition is corrupted however my laptop (where I have windows) is in the service center at the moment so I will try to find another windows machine to get my ext hdd a partition check. I'll let you know later if that solves the problem. If not, I may need your help again :p

thank you for all the suggestions

---

### Post by ekb on 2007-07-08
problem solved. Thank you!

---

