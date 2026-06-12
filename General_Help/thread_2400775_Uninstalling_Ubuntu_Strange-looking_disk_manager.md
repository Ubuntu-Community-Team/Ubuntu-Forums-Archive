---
title: "Uninstalling Ubuntu: Strange-looking disk manager"
date: 2018-09-10
forum: General Help
---

### Post by vashsgirl on 2018-09-10
I'm uninstalling Ubuntu on an older laptop I will be giving away. I think I made a mess when I installed it. From a WUBI install, I uninstalled it from Windows, but it was still on there. So I went through the process of fixing the boot order, and then deleted the partition and extended the C partition to take in the extra space. But I still have this:

[https://www.flickr.com/photos/156189310@N07/albums/72157700889534844/with/42781320540/](https://www.flickr.com/photos/156189310@N07/albums/72157700889534844/with/42781320540/)

I'm not sure why there's a Disk 1 (or why it looks like it has so much space) and what I should do about it, or if I need to worry about it. Can anyone shed some light on this?
Thank you, and please excuse my ignorance.

(The link above also has some basic PC info.)

---

### Post by TheFu on 2018-09-10
wubi has been deprecated/unsupported for years.  Best to just delete all the files from inside Windows, assuming there isn't a WUBI uninstaller.
For help with non-wubi partitioning, the output from **sudo fdisk -l** from 16.04 or later release would be best.  You can make a usb flash drive with 16.04 and boot that to run the command.  Use text, not images, and please use *code tags* so things line up correctly.  BTW, I can't read that image and people using screen readers can't use it at all.

---

### Post by vashsgirl on 2018-09-11
Thanks a lot for your reply. As I explained, it's an older computer, so at the time of installation, WUBI was supported. Yep, I know it's not now, but from what I read on several sites, it was ok to use the WUBI uninstaller. I did that. It appeared to have removed all Ubuntu and WUBI files from Windows 8, but when i rebooted, it went to Grub, and i could access my Ubuntu just like before. So i followed some instructions for repairing boot from within Ubuntu. After that, I was able to boot directly to Windows, and i deleted the Ubuntu partition next to OS (C: ) Primary in Disk Manager, and gave the unallocated space back to Windows. What i hoped would be clear in the photo, but unfortunately was not, was the disk manager. It has Disk 0 (119 GB) containing one Efi partition, one Recovery partition, the OS (C: ) Primary NTFS partition, and a 3.89 GB partition labeled Primary. Below all that is Disk 1 (465 GB) containing a Data1 (I: ) Primary NTFS partition, an Unallocated partition, and a Recovery partition.
I'd like some insight on what Disk 1 is, and if that relates to the Ubuntu i had installed. Thanks again!

---

### Post by mastablasta on 2018-09-11
extend the I: over unalocated disk space and rename it to D: drive.

---

### Post by vashsgirl on 2018-09-12
Thanks!

---

