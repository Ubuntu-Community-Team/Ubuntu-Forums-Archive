---
title: "USB ext3 automount problem"
date: 2007-03-26
forum: General Help
---

### Post by 3saul on 2007-03-26
I have an external USB drive that has an EXT3 partition and a fat32 partition. The fat32 partition automounts read write. The EXT3 mounts readonly.

Any ideas? I know how to mount manually so :) .....
(6.10)

---

### Post by 3saul on 2007-03-26
No responses. Any idea's I can try?

---

### Post by paper0k on 2007-03-26
Try to change permission to the mount point
```
sudo chmod 777 /media/usbdisk
```
replace /media/usbdisk with the correct mount point if it's different ;)

---

### Post by 3saul on 2007-03-26
But doesn't the mount point get created dynamically? Why would the mount point for one partition be created correctly and with the required rights (RW) and another partition on the same drive be created with RO rights?

It makes no sense. Something is wrong somewhere with UDEV.

---

### Post by dcstar on 2007-03-26
> **3saul said:**
> I have an external USB drive that has an EXT3 partition and a fat32 partition. The fat32 partition automounts read write. The EXT3 mounts readonly.

Any ideas? I know how to mount manually so :) .....
(6.10)

Make sure there are no entries for the device in /etc/fstab, and with the EXT3 partition unmounted, do an fsck on it (it may be "dirty" which is forcing a R/O mount).

---

### Post by paper0k on 2007-03-27
> **3saul said:**
> But doesn't the mount point get created dynamically? 
Yes it does
> **3saul said:**
> Why would the mount point for one partition be created correctly and with the required rights (RW) and another partition on the same drive be created with RO rights?
I'm sorry, I don't know why, but it's what pmount (by pmount-hal) does for this type of filesystems

---

