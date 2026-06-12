---
title: "[SOLVED] How to change 'media' on desktop to other names"
date: 2008-07-09
forum: General Help
---

### Post by pedrogent on 2008-07-09
Hello,

I just installed Ubuntu 8.04.1 after wiping 7.10.

I'd like to know the way to change the unfortunate names '52.3 GB Media', '125.7 GB Media', etc. to something more user-friendly.

Here's a screenshot of a part of my desktop.

Thanks a lot.

Pedro.

---

### Post by crossedout on 2008-07-09
External or internal?  What file system?  At any rate, check out:
[https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

That should guide you greatly towards achieving what you want.

-Xout

---

### Post by pedrogent on 2008-07-09
Internal. I've had them saying the right things before (i.e how they're identified in fstab). Perhaps it's because I did an 'alternate' as opposed to a GUI install this time. I don't know.

File system on each of them is ext2.

Thanks a lot for the link. I'll take a look now.

EDIT: still unsure how to do this...

---

### Post by sdennie on 2008-07-09
If they are all ext2, as the guide above says, you can simple use e2label.  For example assuming you want to label /dev/sda1:

```

sudo e2label /dev/sda1 new_name_for_drive

```

I believe you have to reboot before those changes will be fully recognized.

---

### Post by crossedout on 2008-07-09
```
sudo umount <device>
```
You can determine your devices by using:
```
mount
``` or ```
sudo fdisk -l
```

To rename:
```
sudo e2label <device> <label>
```

Example:
fdisk reveals sdb1 is 52.3gb media.
Use the umount command to unmount that volume.
Then run the e2label command substituting <device> with sdb1 and <label> with MyFancyNewNameForMy52.3GB_MediaDrive

-Xout

---

### Post by pedrogent on 2008-07-09
Thanks so much guys. Everything worked as instructed.

Love these forums.

---

### Post by crossedout on 2008-07-09
Glad to help, please mark this thread solved then :)

-Xout

---

### Post by pedrogent on 2008-07-09
One step ahead of ya...

---

### Post by scouser73 on 2008-07-09
Try this for renaming hard drives.

[https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

---

