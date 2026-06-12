---
title: "XP partition won't resize?"
date: 2007-12-17
forum: General Help
---

### Post by michaelzap on 2007-12-17
I have a strange issue that is annoying me:

When I installed Feisty I did it by resizing by XP partition (down to 100GB on a 160GB drive) and using the rest for Ubuntu. When Gutsy was released I decided it was time to give each OS its own hard drive. So I got a new 320GB drive and installed Gutsy on it and then deleted the old Feisty partition on the original drive and resized the XP partition to the full 160GB again.

When I view the XP drive in Gparted or Partition Magic it appears to be 160GB. But within Windows XP the drive still shows up as only 100GB. I've run chkdsk, but the drive doesn't seem to have any problems until after it's booted XP (and then the only problem is that it's smaller than it should be).

I rarely boot into XP anyway, but this bugs me anyway because I feel like I should be able to fix it. Has anyone else experienced this? And if you fixed it, what did you do?

Thanks in advance for your replies.

---

### Post by cyrusrayne on 2007-12-18
I've had some issue with partition resizing myself, notably with Windows.  I can't recall how I may have fixed it, though I know that a lot of it can be done in the MS-DOS prompt using fdisk (though fdisk I've found to be a pain to work with).  Best of luck though :)

---

