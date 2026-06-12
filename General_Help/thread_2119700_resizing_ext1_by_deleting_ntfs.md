---
title: "resizing ext1 by deleting ntfs"
date: 2013-02-24
forum: General Help
---

### Post by linux spartan on 2013-02-24
i have two hard disks on my laptop with windows xp on my primary hard  disk and on my extended hard disk i have ubuntu on 60% of it and windows  on the rest of it excluding the 4GB swapspace but since i dont use  windows much i would like to have ubuntu on the whole extended hard  disk...there is not much on the windows partition as of yet,just about  50 MB occupied...which would be the best way...not necessarily simplest  to go about this without losing data which is my primary concern for the  ubuntu partition

---

### Post by TheFu on 2013-02-24
Copy the Windows data to the main HDD, then delete the windows partition on the 2nd HD, followed by using gparted (boot from other media, not the HDD) to resize the Ubuntu partition as desired.

However, if you have just 1 Ubuntu partition, this would be an ideal opportunity to split /home off onto a dedicated partition. This will make OS upgrades less risky to your personal data in the future. There are other reasons to do this too.
If you do this, then you will need to change the partition type and make a new ext4 file system - NTFS cannot/should-not be used for anything other than pure data under Linux.

---

### Post by linux spartan on 2013-03-05
it worked check my link to solve grub recue error [http://ubuntuforums.org/showthread.php?t=2122396](http://ubuntuforums.org/showthread.php?t=2122396)

---

