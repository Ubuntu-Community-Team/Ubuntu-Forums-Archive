---
title: "Error message when trying to format USB pendrive with the Disks utility"
date: 2017-09-09
forum: General Help
---

### Post by AbleTassie on 2017-09-09
I am getting an error message when I try to format a USB pendrive using the Disks utility. More specifically, when I select "Format Disk" from the menu in the upper right hand corner and also later select "Don't overwrite existing data (quick)", after a while I get an error message box (see screenshot below) that reads: *"**Error formatting disk **Error synchronizing after initial wipe: Timed out waiting for object (udisks-error-quark, 0)." *I get the same error message if I select "Overwrite existing data with zeroes (slow)."

If you look at the screenshot, you can see there are currently 3 partitions on this 32 GB pendrive: two partitions on the ends are free space (5.4 GB and 19 GB) and the partition in the middle (7.3 GB) is formatted as NTFS and labelled Filesystem partition 2.

I would like to put a fully installed Lubuntu operating system on this pendrive. But I do not think I can do it until the drive is 100% free space.

Any idea what I can do?.

Thanks,

A.

[ATTACH=CONFIG]276664[/ATTACH]

---

### Post by AbleTassie on 2017-09-10
I tried the solution suggested at this link [https://itsfoss.com/how-to-format-a-sd-card-or-usb-drive-in-ubuntu-12-10/](https://itsfoss.com/how-to-format-a-sd-card-or-usb-drive-in-ubuntu-12-10/) , which was for a similar problem and error message. But that solution would not work since the "Format to" and the "Tick sign" options were not available in Gparted for my situation. These options were grayed out and could not be selected. 

What did work was Device>Create Partition Table in Gparted; and I selected "msdos" as the new partition table type. The partitions in the pendrive (i.e., "Device") had to be unmounted before doing this. This action created a pendrive that was all Free Space. I then proceeded to put a full install of Lubuntu on the pendrive. That full install seems to work just fine. 

I will mark this thread as [SOLVED].

Thank you (I guess, since there were no views or replies). But I do appreciate this Forum very much and the hard work of the moderators and everybody who keeps it up and going.

A.

---

