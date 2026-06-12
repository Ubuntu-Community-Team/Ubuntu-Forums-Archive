---
title: "How to increase Ubuntu partition on GPT disk"
date: 2016-09-25
forum: General Help
---

### Post by rizzeal on 2016-09-25
I'm trying to increase the size of my Ubuntu partition without deleting any data. The disk has in total 3 partitions, first the Uefi partition, then the Windows partition and at last we he have the Ubuntu partition.I shrunk the windows partition by 10 GB so now there is 10GB free space in between the Windows and Ubuntu partitions.I would like to add this 10GB to the Ubuntu partition. A lot of the guides say to use Gparted partition editor, but I can't see my drive in there. (I guess it's because it has a GUID partition table?). I am at a loss on how to do this now. Do i have to convert my disk to MBR or is there any way to reinstall ubuntu and choose a bigger partition and afterwards restore my current files from a backup?Thanks for the help!

---

### Post by oldfred on 2016-09-25
You need to use live installer or gparted live system.
Not sure if live installer has new enough gparted. The version installed in my 16.04 is 25.0, but I can only use that for my sdb drive, as you cannot change mounted partitions. (in gparted you see little key icons).

 gparted should be at least version 0.24.0-1 to recognize NVMe devices
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

I do not like moving partitions left as that takes a lot longer as all data must be copied and it can then be more dangerous as any system power failure or reboot totally corrupts partition. So make sure you have good backups.

---

### Post by rizzeal on 2016-09-26
Hello, thanks for your reply. It finally worked, I was using a live installer for Ubuntu 14.04, after switching to a live installer for 16.04 it picked up the nvme drive without any problems.

---

