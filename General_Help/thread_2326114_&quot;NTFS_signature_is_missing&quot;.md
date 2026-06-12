---
title: "&quot;NTFS signature is missing&quot;"
date: 2016-05-28
forum: General Help
---

### Post by raphael18 on 2016-05-28
Hi,

When mounting an internal SDD hard drive (live session Ubuntu via USB) I get the error message:

"NTFS signature is missing
Failed to mount '/dev/sda4' : Invalid argument
The device 'dev/sda4' doesn't seem to have a valid NTFS."

I believe /dev/sda4 is the correct partition to mount (from the result of fdisk -l), its type is "Microsoft basic data" and the disk /dev/sda is disklabel type gpt and 512 bytes sectors.

The command I'm doing is 'sudo mount -t ntfs-3g /dev/sda4 /mnt/ssd' I have created the directory ssd in /mnt and checked that the package ntfs-3g is installed.

I read a LOT of posts on that issue but wasn't able to find a solution... I did a shutdown /s on Windows (Windows 8) before booting Ubuntu. The internal hard drive is SSD, does that has to do with this error?

Thanks!!

---

### Post by TheFu on 2016-05-28
Win8 and later don't always close a file system down at shtudown. There are lots of how-to guides explaining how to disable that feature of Windows..  Check some Windows-centric websites if you can't find the settings in windows to disable that.  Don't remember the name they gave it and it may have nothing to do with this specific issue, but it **is enabled** by default in Windwos. Wouldn't hurt to run the Windows scandisk/chkdsk tools on that partition too. Use the disk repair tools for the OS that created the file system to avoid data loss and other surprises.  NTFS scans happen on Windows.  EXT2/3/4 happen on Linux.

If you could, please post the output from **sudo parted -l** here.  Also, please, please, please, please, use code tags to things line up. This will help with some data.

---

### Post by raphael18 on 2016-05-28
Hey, thanks!

So here is the partition table on /dev/sda

```
Model: ATA SAMSUNG MZMTE128 (scsi)
Disk /dev/sda: 128GB
Sector size: 512B/512B
Partition table: gpt
Disk flags:

#1 1049kB-379MB ntfs Basic data partition hidden, diag

#2 379MB-588MB fat32 EFI system partition boot, esp

#3 588MB-722MB Microsoft reserved partition msftres

#4 722MB-122GB Basic data partition msftdata

#5 122GB-128GB ntfs Basic data partition hidden, diag
```

Sorry, don't see rich text edit options on mobile....!

So weirdly it seems the partition 4 (the main one in terms of size, so the one I want to mount I guess) doesn't have file system specified. Do you think this is due to this file system not closed down at shutdown on Windows 8?

Thanks again, sorry for the formatting here

---

### Post by oldfred on 2016-05-28
Easy to add code tags with the Forum's advanced editor and # icon.
 Not sure with phones what you get. Bit more difficult to highlight.

       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

### Post by TheFu on 2016-05-28
Often it is easier to use the normal "quote" button, but manually change it into "code" - at least that's how I do it.  I never use my tablet/phone anywhere a login is needed. Not safe.

---

