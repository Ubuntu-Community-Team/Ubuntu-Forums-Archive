---
title: "Dual Boot - Win2000, Gutsy Already Installed"
date: 2008-02-19
forum: General Help
---

### Post by 64mgb on 2008-02-19
I have Gutsy installed, used the GParted Live CD to resize the primary partition, used the extra space to create a new NTFS (also tried FAT32) partition, and then tried to load Windows 2000 to the new partition.  The Windows 2000 setup floppies all load fine, and then it starts to work off of the CD and asks if I want to install Windows 2000 now.  After I hit ENTER, it think for a few seconds, then stops with a message that says "Setup did not find any hard disk drives installed in your computer."

Any ideas?  As I was typing this, I remembered that I had problems with another computer a while back because I was using a SATA drive, and this is a SATA drive.  Do you think that could be the problem?  If I remember right I had to do something with some SATA drivers on a floppy before I could load Windows 2000.

Thanks,
Rich

---

### Post by 64mgb on 2008-02-19
I guess I should have done more research before posting...that's exactly what was wrong.  I had to tell setup that I wanted to install the SATA drivers off a floppy.

Rich

---

