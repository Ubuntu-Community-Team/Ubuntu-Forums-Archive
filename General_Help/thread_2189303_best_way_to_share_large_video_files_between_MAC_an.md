---
title: "best way to share large video files between MAC and ubuntu"
date: 2013-11-21
forum: General Help
---

### Post by borderblu on 2013-11-21
I'm working on a documentary and using linux, my partner a mac. I would like to back up the project on my external hard drive (Toshiba canvio 3.0, 500 GB). 

I want to use exFat i think, any suggestions.....

I've been follwing this tutorial to install exfat functionality and gpated:

[http://www.unixmen.com/how-to-format-usb-to-exfat-in-linux/](http://www.unixmen.com/how-to-format-usb-to-exfat-in-linux/)

---

### Post by borderblu on 2013-11-21
P.S. this is a video doc, so the files may potentially get very large

---

### Post by nerdtron on 2013-11-21
Format the drive as NTFS and install a plugin in Mac so you can read/write NTFS drives.
I think it is NTFS-3g or paragon to enable write in Mac.

---

### Post by jamesisin on 2013-11-22
There are a variety of extfs solutions for the Mac:  [http://apple.stackexchange.com/questions/29842/how-can-i-mount-an-ext4-file-system-on-os-x](http://apple.stackexchange.com/questions/29842/how-can-i-mount-an-ext4-file-system-on-os-x)

I'm not convinced using a Windows file system to share between a Mac box and a Linux box is the best solution.

Since FAT can manage file sizes up to 4 GB you might partition one FAT partition and then one ext/ntfs partition specifically for the larger files.

Also, reading is much easier.  So if the Mac doesn't need write access you have more options.

---

### Post by Lars Noodén on 2013-11-22
> **jamesisin said:**
> I'm not convinced using a Windows file system to share between a Mac box and a Linux box is the best solution.

Nor am I.  Especially since the FAT system are prone to data loss and NTFS will get slower and slower it gets unavoidably fragemented as you use it.  Neither are good with large files.

If you format the drive to HFS+ using the Macintosh and turn off journaling for that partition, you can read and write from both systems.  I have done this for many years.  

```

diskutil disableJournal /Volumes/somepath/

```

Then you will be able to read and write from both systems.  Ubuntu needs no added drivers or utilities.  

But if you plan to do various maintenance activities, including formatting, on Linux you should consider adding hfsplus, hfsprogs, hfsutils to your installed packages.

As with any system, keep regular backups.

---

### Post by borderblu on 2013-11-23
since we don't have any files over 4GB we went with FAT....

---

### Post by Lars Noodén on 2013-11-23
If you are going with exfat, be religious about properly unmounting the drive before disconnecting and about backups.  But then that's important for any filesystem on removable devices.   If you have trouble anyway then consider HFS+.   It is the Macintosh's own native filesystem and Ubuntu works with it well.

---

