---
title: "Flash Drive Copy &amp; Paste?"
date: 2018-02-20
forum: General Help
---

### Post by nedjinski on 2018-02-20
I have a desktop running 16.04 etc 

I have a USB flash drive with files on it formatted to NTFS on a Windows 10 machine.
I have a USB flash drive formatted to ext2 using gparted on the desktop machine.

I want to transfer files from the NTFS drive to the ext2 drive.

When I insert both flash drives into the desktop machine, windows open for both and I can see the contents of the NTFS drive. I can also select "Copy" of the the contents of the drive.
When I look at the ext2 drive window there is no option to "Paste" - the option is greyed out.

Is this not a possibility? Or am I doing it the wrong way?

Thanks for your help.

---

### Post by yancek on 2018-02-20
Check the ownership/permissions on the ext2 drive, you may need to change that or use sudo.

---

### Post by ajgreeny on 2018-02-20
A mountpoint of an ext~ disk will by default be owned by root so you need to find the mountpoint and then run ```
sudo chown $USER /media/username/usbdisk
```
You can find the correct mountpoint for the usbdisk by inserting the flash drive and then looking in /media/username.

---

### Post by nedjinski on 2018-02-20
Thank you very much - that worked - I used nautilus. Is that the best tool for this process?

---

### Post by ajgreeny on 2018-02-20
Use whichever file manager you prefer, usually the one that comes with your OS.

Or you can use the command line in a terminal if you are willing and able to do so; it is not nearly as difficult to use commands in the terminal as many users believe it to be, and it is well worth learning more about doing so.

---

