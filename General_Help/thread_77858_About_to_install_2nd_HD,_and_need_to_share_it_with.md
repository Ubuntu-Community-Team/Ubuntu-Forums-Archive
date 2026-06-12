---
title: "About to install 2nd HD, and need to share it with XP"
date: 2005-10-17
forum: General Help
---

### Post by dishbert on 2005-10-17
What would be the best way to handle this?  My initial thought is to format it with XP to FAT32.  The current HD is 80 G, with the XP and Breezy OS's evenly divided.  The new hard disc will be 200 G and used mainly to store media files:  mp3's, mpegs, and video.

---

### Post by seldenthuis on 2005-10-17
[QUOTE=dishbert]My initial thought is to format it with XP to FAT32.[/QUOTE]

That's what I did too. You could make it an NTFS filesystem and enable NTFS-write support in your kernel, but that's probably not a good idea since it's still unstable. I believe there's also a program which gives you ext2-support in Windows, but I don't know what it's called and how useful it is.
I would just go with FAT32.

---

