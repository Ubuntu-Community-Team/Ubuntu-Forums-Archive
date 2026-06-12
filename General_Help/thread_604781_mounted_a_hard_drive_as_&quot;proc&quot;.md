---
title: "mounted a hard drive as &quot;proc&quot;"
date: 2007-11-06
forum: General Help
---

### Post by chocolatetoothpaste on 2007-11-06
Ok, so I was trying to mount my 250gb hard drive, and when I was editting my fstab file, I typed "proc" as the file system type.  then I did a "sudo mount -a".  After realizing my mistake, I fixed the fstab file, restarted, and now, my hard drive doesn't show up under /dev.  (it's a secondary drive for storage.  the os is on the primary drive).  So, basically I'm asking, am I screwed?  Did I call the fs, or is this fixable?

---

### Post by Happy_Man on 2007-11-06
Install Gparted ```
sudo apt-get install gparted
``` and use that to see if your HDD is even recognized. If it isn't, boot the livecd and check. If it is recognized, you'll be able to tell with Gparted whether the data's still there or not.

---

