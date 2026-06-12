---
title: "can't share ntfs drive with other computer profiles in nautilus"
date: 2015-02-05
forum: General Help
---

### Post by sgian on 2015-02-05
I have Ubuntu 14.10 dual boot with two internal harddrives.  This computer stays on ubuntu most of the time, but I formatted the secondary hard drive in ntfs with gparted so that it can be accessed from both ubuntu and windows.  I can mount it fine with my administrative profile, but I can't share it with other profiles.  Permissions in properties just immediately change back to no access for group and others.  It will not go into other settings to share the files and folders.  Samba doesn't stay shared either after reboot, but I would rather fix the nautilus issue right now.

---

### Post by sgian on 2015-02-05
If there is no fix for sharing ntfs drives with other profiles on the same computer, what is a better format to use that will be recognized by both windows and linux?

---

### Post by Mike_Walsh on 2015-02-05
Hallo, sgian.

As you no doubt know, ntfs is one of only two file formats that Microsoft will permit Windows to recognise. On the other hand, Linux will recognise just about any file format there is. 

The other file format that Windows WILL recognise is FAT 32, but there IS a size limit for Fat 32-formatted drives; IF, that is, you are trying to format it with Windows (somewhere around 32 GB, I believe).

However, with Linux, you CAN format drives up to 8 TB in size with FAT32, in such a way that Windows will still be able to read it. Have a look at these links, and see if they will answer your needs:-

[http://techcosupport.com/press/maximum-size-of-a-fat-32-partition/](http://techcosupport.com/press/maximum-size-of-a-fat-32-partition/)

[http://www.dedoimedo.com/computers/windows-fat32.html](http://www.dedoimedo.com/computers/windows-fat32.html)

[http://www.pendrivelinux.com/large-external-usb-hard-drive-fat32-format-utility/](http://www.pendrivelinux.com/large-external-usb-hard-drive-fat32-format-utility/)

Hope that helps.


Regards,

Mike. ;)

---

### Post by Morbius1 on 2015-02-05
Choose one of the ntfs partitions:

[1] Run the following command to find the correct uuid number:
```
sudo blkid -c /dev/null
```
[2] Create a mount point for a partition:
```
sudo mkdir /media/Data
```
[COLOR=#0000cd]*You can mount it anywhere just don't use /media/your-user-name/Data*[/COLOR]

[3] Edit /etc/fstab and add the following line - adjusting for the correct UUID and mount point:
```
UUID=DA9056C19056A3B3 /media/Data ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```
[4] If you currently have the partition mounted unmount it.

[5] Then run this command to remount the partition:
```
sudo mount -a
```

If it comes back to the prompt it mounted successfully. From now on this partition will mount to that mount point at boot time.
[B]
umask=000[/B] will make it so every local user will have access.
**uid=1000** will make you the owner of the partition.

---

### Post by sgian on 2015-02-05
thank you both for your help.

---

