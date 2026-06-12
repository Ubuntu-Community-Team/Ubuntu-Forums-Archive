---
title: "How to transfer files from Ubuntu to Windows"
date: 2016-04-19
forum: General Help
---

### Post by ChristmasPi on 2016-04-19
I have some image files on my Ubuntu drive that I would like to transfer to a Windows 7 PC via a USB stick.  In the past, I would just email them, but the Win 7 PC is off the network and cannot be joined.

Is there any way for me to transfer these image files from Ubuntu to Windows 7 using a USB stick?

Thank you

---

### Post by DuckHook on 2016-04-19
Both OSes will read the USB stick so long as the USB stick is formatted to a commonly understood file structure. Unless you reformatted your USB stick after purchasing it, it should already be formatted so that both OSes can read it. Simply copy the images onto the USB stick from your Ubuntu computer and then copy them back onto your Windows computer.

---

### Post by T.J. on 2016-04-19
Yes, of course.  Simply format the USB stick on Windows if needed.  Then take it and plug it in to the Linux machine. It can read Windows drives.  Copy the files and then eject the usb.  Plug it into the Windows machine.  Copy files.  Done.

If you have problems, please let me know.

---

### Post by SeijiSensei on 2016-04-19
You can format the device from Linux, too.
```
sudo mkfs -t vfat /dev/sdb1
```
would create a FAT32 filesystem on the device if it's assigned /dev/sdb.

Note, though, that FAT32 has a filesize limit of 2 GB.  If you have larger files than that, format the device as NTFS on Windows, then insert it into the Linux machine and write to it there.

---

