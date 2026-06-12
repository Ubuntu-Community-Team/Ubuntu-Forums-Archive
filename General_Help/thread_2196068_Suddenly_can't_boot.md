---
title: "Suddenly can't boot"
date: 2013-12-27
forum: General Help
---

### Post by x1a4 on 2013-12-27
Hello,

On Xubuntu 12.4 everything worked fine.  Then, I moved some files to a Seagate BackupPlus portable drive.  I then shut the laptop down.  When I tried to boot again I got a message stating that an operating system was not found.  I booted to a thumb drive and all the files are there.  The 'boot' flag is set for the UEFI partition as normal.  The files I moved were all videos from the /home partition which only containes user files.  No operating system files were on it.  

Any advice helping me to diagnose and solve this is greately appreciated.  Thank you.

---

### Post by egeezer on 2013-12-27
One customary shot at repair is (since you seem to have a thumb drive to boot to) is to boot the live USB and mount the Ubuntu partition:
```
sudo mount /dev/sda /mnt
```
then run grub-install:
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot and run ```
sudo update-grub
```

That works, unless some files have been deleted or corrupted.  In that case,
```
                         sudo mount /dev/sdXY /mnt   
``` and then
```
                         sudo grub-install --boot-directory=/mnt/boot /dev/sdX   
```

---

### Post by fantab on 2013-12-28
Was the backup drive plugged in when you booted Ubuntu and got the error?
If in your UEFI/BIOS the HDD boot order is set to boot USB first, it WILL boot first. And since the USB backup drive is NOT bootable you get the error message you got.
Unplug the USB and boot again.
If none of the above is true then perhaps you should follow the steps in previous post and re-install grub or simply use [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair").
Is there another OS in the picture?

---

