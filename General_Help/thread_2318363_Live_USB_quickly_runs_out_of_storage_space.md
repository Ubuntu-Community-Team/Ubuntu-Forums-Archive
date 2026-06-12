---
title: "Live USB quickly runs out of storage space"
date: 2016-03-25
forum: General Help
---

### Post by vyco10 on 2016-03-25
I have Ubuntu MATE 14.04 on a 4GB flash drive. When I used the universal installer I set persistence to max allowable, which is around 2.7GB. It doesn't make sense to think it, but is that what's causing me to run into storage problems? Or is the Ubuntu system just taking up too much of the space? Is there something I can do to create more space on the drive I have or do I just need a bigger drive?

TIA

---

### Post by sudodus on 2016-03-25
- What storage problem is it?
- Is your casper-rw partition full or almost full?
- Are there personal data files or installed programs?
- Have you remembered to remove files from the trashcan?

If you really need more space for installed programs and personal data files, and many people do, then you need a bigger drive. If you get a 16 GB drive (or bigger), you can get a much faster drive too. Even in a USB 2 port, the system will be faster with a fast USB 3 pendrive.

See the following links

[Notes about size](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_size)

[Link to USB 2 and USB 3 speed tests for installers](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)

You can try mkusb to make a persistent live drive with a ***casper-rw partition*** (instead of a casper-rw file). This makes it possible to take full advantage of the big USB pendrive. There is also an option to share the available drive space between the casper-rw partition for the linux system's persistence and an NTFS partition for storing files that will be available when the pendrive is connected to a computer running Windows. See these links:

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by C.S.Cameron on 2016-03-25
With only a 4GB drive, a persistent partition will not be an advantage.
2.7GB is the most persistence you can get.
It should be enough for a while if you don't install a bunch of stuff.
Do not do a software update, this will fill the drive quickly.

---

