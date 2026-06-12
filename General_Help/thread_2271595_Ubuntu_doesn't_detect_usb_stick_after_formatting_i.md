---
title: "Ubuntu doesn't detect usb stick after formatting it"
date: 2015-03-31
forum: General Help
---

### Post by leonardo18 on 2015-03-31
I formatted my 16GB usb drive with the Disks utility, but now I can't access it, it is shown in the Disks menu (pic related) but can't see it in the bar on the left with the other drives.
Also when I access my Windows 7 partition (I'm dual booting) it tells me that drive needs to be formatted and then tells me it cannot format it

---

### Post by ajgreeny on 2015-03-31
Perhaps worth trying gparted to see what that can find out about the drive.  You can do this either from a live system or install it to your Ubuntu OS.  Also show us what the output is from terminal command ```
sudo fdisk -l
```

You will need to right click on the partition on the disk, if it actually has one already to unmount it and then can try to format as a new partition.  I have never used the Disks utility to format a drive but use gparted a great deal; it has never let me down in any way.

---

### Post by dcstar on 2015-04-05
> **leonardo18 said:**
> ...........
Also when I access my Windows 7 partition (I'm dual booting) it tells me that drive needs to be formatted and then tells me it cannot format it

If Ubuntu and Windows cannot format it then it is possibly a faulty device.

---

