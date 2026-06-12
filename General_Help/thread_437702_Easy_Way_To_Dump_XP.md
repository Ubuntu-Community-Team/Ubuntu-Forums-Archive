---
title: "Easy Way To Dump XP?"
date: 2007-05-09
forum: General Help
---

### Post by ddougan on 2007-05-09
Hello all,

I have been using Ubuntu for the past couple of days (on a xp dual boot) and I have grown to love this distro. I was hoping for an easy way to completely hand over my XP partition to my Linux partition without losing any data on the Linux end (I already backed up my data on the NTFS partition.) What's the best way of doing this? From the research I've done, it sounds like Gparted will work for the scenario? Is this true? If so/not what method do you suggest?

Thanks.

---

### Post by Schalken on 2007-05-09
Yes Gparted will work from the Ubuntu livecd, however just to be sure try the Gparted livecd from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) . It has more functionality and I have found it more reliable.

Just open GParted and click on your windows partition (NTFS (default) or FAT32) and delete, then click on your Linux parition (EXT3 (default) or ReiserFS) and resize to fill it up. You may need to move your swap partition (linux-swap) first.

Good luck.

---

