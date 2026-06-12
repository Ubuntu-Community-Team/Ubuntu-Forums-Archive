---
title: "How do I delete lost+found folder from external hard disk?"
date: 2015-01-20
forum: General Help
---

### Post by arroy_0209 on 2015-01-20
In my ubuntu 12.04 I am trying to create bootable usb-drive but unfortunately the external hard drive which I thought was empty, first showed this folder:  .Trash-1000 which I removed following suggestions got from google search. After this I am stuck because a new lost+found folder is apearing in that external drive (don't know how it got created in the first place) which I failed to erase using rm -rf command, or formatting using the disk utility application which comes with ubuntu. Note that only root has permission to operate (drwx------) on that folder. How can I remove this folder and make the external hard drive clean? How will installation process be affected in case I keep this folder and write the sutable file got using the unetbootin program?

---

### Post by sudodus on 2015-01-20
Those are linux system directories.

Unetbootin works well with the FAT32 file system. It might work with ext2, but I have never tried. Anyway, if you use FAT32, there will be no linux system directories.

See this link [https://help.ubuntu.com/community/Installation/FromUSBStick#Unetbootin](https://help.ubuntu.com/community/Installation/FromUSBStick#Unetbootin)

---

### Post by arroy_0209 on 2015-01-20
Am I allowed to change filesystem? If I try to format using disk management utility, it shows that filesystem  on external hard drive is EXT4. Can I change filesystem to FAT32 myself for the external hard drive?

---

### Post by sudodus on 2015-01-20
Most people would make a USB boot ***pendrive***, but it is possible to use a hard disk drive too for that purpose. I would suggest that you make a small FAT32 partition in the beginning of the drive for the live system. Then you can have a suitably sized casper-rw partition with ext4 for persistence and the main part of the external drive can be a data partition (for storage of data) with the ext4 file system too.

If you intend to access it from Windows (if you have Windows in the internal drive), you should do it in a different way. Windows can only use the first partition in a USB drive. One solution would be to make the FAT32 partition big enough for the data you want to share with Windows. Another solution would be to have a first partition with NTFS (file system) for the data you want to share with Windows. The have a suitably sized second partition with FAT32, where you have the live system, and then you have a casper-rw  with ext4 for persistence (if you wish).

Or would you rather make a regular installed Ubuntu system in the external drive. In that case you need a DVD disk or USB pendrive for the installer (to use Unetbootin to transfer the Ubuntu system from the iso file to the install media (DVD or pendrive). And then boot the computer from the install media and install into the USB hard disk drive.

 			 			[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389") 				


-o-

***gparted*** is a good tool to create/change/delete/resize partitions and to fill them with filesystems. gparted is included in the Ubuntu live systems. You should boot from another drive, not the drive you want to change (edit partitions). I think it is easier to use gparted than 'disks'.

***[COLOR=#ff0000]Warning[/COLOR]***: it is risky to edit partitions and install operating systems. ***Backup*** all your personal data to another drive before - something may go wrong and you need to restore the data.

---

