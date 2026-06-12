---
title: "NTFS resize help"
date: 2014-01-18
forum: General Help
---

### Post by skibum3027 on 2014-01-18
I was using this forum post ([http://ubuntuforums.org/showthread.php?t=1244058](http://ubuntuforums.org/showthread.php?t=1244058)) as a guide to shrinking an NTFS partition on a drive with bad sectors (so GNU parted won't touch it as far as I can tell) and got to the part where I need to use fdisk to modify the partition table. But apparently fdisk doesn't work with GPT (it's a 3 TB hard drive), and refers me back to GNU Parted, which I can't make work with bad sectors. Can anyone tell me a way to modify the partition table for this drive?

Thanks in advance for the help, and I can run commands and post responses as requested!

---

### Post by TheFu on 2014-01-18
gparted
or 
parted

However, the best way to manage NTFS is from Windows.

---

