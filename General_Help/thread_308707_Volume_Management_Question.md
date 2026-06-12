---
title: "Volume Management Question"
date: 2006-11-28
forum: General Help
---

### Post by gladelson on 2006-11-28
I am new to Ubuntu but not to Linux in general. I have an Ubuntu 6.1 install on a 15 GB partition on a 160 GB disk (there is also a 10 GB Win2000 NTFS partition, and a Linux swap partition). There is also a second currently unpartitioned 160 GB disk. I want to use this box as a media/file server. I have Samba working correctly. I want to partition the remaining space on the first disk (about 135 GB) as a single volume and the entire second disk and join those two as a single linear storage object (which would be about 295 GB) on a single moint point (No RAID). Do I have to use a volume manager like EVMS or LVM to do this, or is there another simpler way? Any suggestions would be appreciated.

G.

---

### Post by wpshooter on 2006-11-28
My guess is that you could use LVM to do this, but my thoughts would be that the ideal time to have done this would have been while you were originally installing Ubuntu !!!

---

