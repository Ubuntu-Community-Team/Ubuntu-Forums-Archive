---
title: "Can't delete the partition from GParted of unmounted device."
date: 2020-06-06
forum: General Help
---

### Post by tmpidkalwar on 2020-06-06
Hi,

I have a SD card, which is showing under /dev/mmcblk0. I unmounted the device and trying to delete the partition from GParted, but i am not getting enabled option to delete the partition. The screenshot is attached. Could you please help me delete the partition?

---

### Post by tea for one on 2020-06-07
Your SD card is not showing a partition.

/dev/mmcblk0 is the SD card itself.

If you had a partition, it would be /dev/mmcblk0p1

---

### Post by Impavidus on 2020-06-08
If you want to delete the filesystem, you can create a new partition table. If it doesn't work, you could try to overwrite the first megabyte or so of the card with zeros. dd can do it, but it may be safer to use a tool like mkusb.

---

