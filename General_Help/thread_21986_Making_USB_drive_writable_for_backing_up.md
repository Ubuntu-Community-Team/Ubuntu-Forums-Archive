---
title: "Making USB drive writable for backing up"
date: 2005-03-25
forum: General Help
---

### Post by Tlanuwa on 2005-03-25
Hiya! My Windows/Linux box recently crashed and burned (on the Windows side of things), so I've decided to wipe it all and install Linux, and only Linux, fresh.

The problem is that I have a LOT of data organized into a huge folder system in Windows. I also have a USB key that I'd like to back it up to, which Ubuntu Live finds, and allows me to view, and allows me to write to as root. The problem is that all I can figure out how to do is copy the files basically one-by-one, and as I don't want to recreate all those directories by hand, I'd hoped to just "drag and drop" all of it.

The problem is I don't have write access as the default user in the GUI, and I can't figure out how to fix this.

Any suggestions?

Thanks,
John

---

### Post by nemin on 2005-03-25
[QUOTE=Tlanuwa]
The problem is that I have a LOT of data organized into a huge folder system in Windows. I also have a USB key that I'd like to back it up to, which Ubuntu Live finds, and allows me to view, and allows me to write to as root. The problem is that all I can figure out how to do is copy the files basically one-by-one, and as I don't want to recreate all those directories by hand, I'd hoped to just "drag and drop" all of it.[/QUOTE]
This is the most simple solution I guess:
[list]
[*]Mount the windows partion, example: ```
sudo mount /dev/hda1 /mnt/windows
```
[*]Copy all files from the mounted partition to the USB-device, example ```
sudo cp -R /mnt/windows/file /mnt/usbstick
[/list]
```
Please let know when you stuck on this. :)

---

