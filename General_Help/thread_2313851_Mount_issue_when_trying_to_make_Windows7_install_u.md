---
title: "Mount issue when trying to make Windows7 install usb"
date: 2016-02-16
forum: General Help
---

### Post by Alex_Chobanov on 2016-02-16
Hello,
I have to reinstall Windows, which obviously is the easy part, because I am stuck on creating a bootable usb installer. Until today using 'dd' always worked for me.
```
dd if=<iso> of=<disk> oflag=direct bs=1048576
```

Today, however it didn't work, the PC was stuck on blinking _ after BIOS and no booting at all, no errors as well. So I figured to try something else and WinUSB was the first thing to come out of google. So installed it I did and used it as:
```
sudo winusb --format <iso> /dev/sdc
```

And it spits: 
```
Formating device... 
Mounting... mount: you must specify the filesystem type 
Error occured ! 
Syncing... 
Cleaning... 
Umounting and removing '/media/winusb_iso_1455641284_12456'... 
umount: /media/winusb_iso_1455641284_12456: not mounted 
Umounting and removing '/media/winusb_target_1455641284_12456'... 
umount: /media/winusb_target_1455641284_12456: not found
```

I read information regarding the mounting and when the usb has partition ( say ntfs ) and I try to mount it as
```
mount /dev/sdc1 /media/Kingston
```
It is working. USB is working properly as well, because I can copy, paste and use it when it is mounted.

What to do?

---

