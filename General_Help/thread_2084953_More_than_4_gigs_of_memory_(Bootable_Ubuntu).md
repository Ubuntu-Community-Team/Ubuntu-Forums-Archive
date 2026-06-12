---
title: "More than 4 gigs of memory (Bootable Ubuntu)"
date: 2012-11-16
forum: General Help
---

### Post by KhailzXsniper on 2012-11-16
The USB bootable ubuntu only has 4 giigs of memory for the casrper and im wondering if theres a way to have more memory because once you use all the space theres no way to use it agian.

---

### Post by efflandt on 2012-11-16
A live/install iso on bootable USB is a FAT32 file system which is limited to maximum file size of just under 4 GB.  But a casper-rw file is a loop mounted ext2 file system, so the size of the casper-rw file does not reflect how much data is on the loop mounted file.  So just because casper-rw is about 4 GB does not mean that it is full or that you cannot delete files from it to make room for other files.

There is supposed to be a way to have the live/install iso automatically use a separate partition with a casper-rw label, but I have not figured out how to do that.  Then as an ext2 or whatever partition, the persistent data could be any size.

But really that is insecure, since anyone who boots it can get into Linux without a password with root access to anything.  So it would be better to have large enough flash (8 GB minimum recommended) to do a regular install instead of using the live/install iso.  That would also allow you to use proprietary video drivers and do kernel updates, etc. that you cannot do with the live/install iso (without remastering your own iso), because the live/install iso initially boots from a fixed squashfs file system before persistent data is mounted.

---

### Post by oldfred on 2012-11-17
Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)


   [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)


       
 Large persistent - C.S.Cameron post 6 & 7
[http://ubuntuforums.org/showthread.php?t=2041679](http://ubuntuforums.org/showthread.php?t=2041679)

---

