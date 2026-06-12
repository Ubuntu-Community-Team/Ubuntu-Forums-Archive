---
title: "Unlock my USB drives?"
date: 2007-09-08
forum: General Help
---

### Post by JusticeZero on 2007-09-08
I use USB flash drives and a USB hard drive. Often Ubuntu decides that I do not have write permission to change the contents of these drives. Obviously this makes the USB drives useless to me. How do I make the damned things open so I can write files to them?

---

### Post by K.Mandla on 2007-09-08
Check the contenst of your /etc/fstab file, and make sure you have access to those drives. You can see the identifier of your drive with 

```
sudo fdisk -l
```
Make sure the identifier is listed in fstab, and that the drive has a users identifier after it.

---

### Post by vanadium on 2007-09-08
USB drives are and should not be in /etc/fstab.

* USB drives are automatically mounted when you insert them with permissions for the user. If that is not the case, then check in "System - Preferences - Removable media: Storage tab" that the first option is checked.

* ntfs formatted USB's cannot be written to because the specifications of the format are kept secret by microsoft. There is currently additional software, ntfs-3g, that allows to write ntfs, but it needs to be installed.

* If you external drive is ext3 formatted, then make sure that the directories where you want to write have the proper permissions set.

---

### Post by JusticeZero on 2007-09-08
Well, the big one seems to be NTFS. Would it operate happily if I formatted it to FAT32 or some other Windows-readable format of which I am not yet aware? (Part of why I use them is to carry files around, and usually end up acessing them on Windows whn away from home)

---

### Post by vanadium on 2007-09-09
You have the widest "compatibility" with fat32. Windows 98, Windows ME, Windows NT, Windows 2000 ... all read it, and also Apple reads it (I think) right out of the box.

For USB sticks, small volumes, I would not hesitate and keep them in fat32. For larger drives, you need to consider whether the 4GB limit of fat32 is a problem or not. If it is a problem, go for ntfs, but then install ntfs-3g (sudo apt-get ntfsconfig) to be able to write them under Linux. This will be compatible with most modern Windows systems out there, but I guess Apple cannot read this.

---

