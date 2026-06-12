---
title: "Can't mount on external hard drive"
date: 2015-11-11
forum: General Help
---

### Post by rezbd on 2015-11-11
I can't access to my external HDD from Lubuntu 15.10, 64 bit. It shows the following error

[[IMG]http://i.share.pho.to/a2edb016_c.png[/IMG]]("http://pho.to/9s2oR")

I can mount the drive from windows 7

Please let me know what to do. Thanks.

---

### Post by sandyd on 2015-11-11
Master File Table (MFT), and Master File Table (MFTMirr) are not consistent.

Can either be fixed by doing a disk repair in Windows, or running the following in Ubuntu.
As always, please ensure backups of the drive are available before running.
```

sudo apt-get install ntfs-3g
sudo ntfsfix /dev/sdb1
```

Note that "/dev/sdb1" is based on the picture you posted. If you have reconnected the drive, or added additional drives, it can change.

---

### Post by rezbd on 2015-11-11
It has been fixed! Thanks a lot sandyd. :-)

---

