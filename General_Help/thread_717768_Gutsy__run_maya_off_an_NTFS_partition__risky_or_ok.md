---
title: "Gutsy : run maya off an NTFS partition : risky or ok?"
date: 2008-03-07
forum: General Help
---

### Post by skullmunky on 2008-03-07
The situation is this: a strange packard bell laptop that has some quirk where you can't install GRUB onto it because the crippleware version of Windows it comes with stores special authorization info in the MBR or something.  anyway, the solution we have is ubuntu on a 4GB flash drive, which works fine, though there's a lot of hiccups as the file access isn't so fast.  since that's not a whole lot of space, the idea is also to store a lot of documents in the windows user's directory on the hard drive (which is NTFS).  so far, so good, but i just want to check if there's any degree of risk in using NTFS r/w heavily, and how much risk there is.  

and if it's a good idea to put the whole /usr/autodesk/maya application directory on this ntfs hard drive too, since that directory is huge.  

(crazy, i know)

---

### Post by PmDematagoda on 2008-03-07
Well, in my personal experience I found the ntfs-3g drivers to be rather stable. But there still maybe a small risk as well, so in any case try and make regular backups of your data before doing that.

---

