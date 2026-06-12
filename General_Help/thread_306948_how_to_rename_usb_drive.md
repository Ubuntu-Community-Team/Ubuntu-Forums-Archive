---
title: "how to rename usb drive?"
date: 2006-11-25
forum: General Help
---

### Post by zardoz on 2006-11-25
Hy!

How do I rename an usb drive under Linux?
sudo mv /media/USB\ Disk /media/usb_disk
gives me Device or resource busy
I tried this for several FAT formated usb sticks and usb harddrive. Never worked.

---

### Post by syadnom on 2006-11-25
you may add a section in one of the udev config files to mount your usb drives to specific directories and associate those directories with the serial number of the drive.  this way every different flash drive you used could have a different directory or your usual one could have a specific directory and others would mount to where they mount now.

im not on ubuntu right now and osx doesnt use udev so i cant help you more right now

---

### Post by zardoz on 2006-11-26
Hm, isn't there an easier way ... 
When I rename the drive under Windows (simply rename it in the file browser), it is also renamed under Linux.
So it seems to me, that these usb drives have real drive names (saved on the drive) and are not just associated with a name via their serial number or so.

---

### Post by zardoz on 2006-11-26
bump

---

### Post by shin on 2006-11-26
A little harder as in windows and depends on filesystem you use on usb drive.

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by zardoz on 2006-11-26
Thanks a lot ... I am wondering why I didn't find that ... not my day.

---

