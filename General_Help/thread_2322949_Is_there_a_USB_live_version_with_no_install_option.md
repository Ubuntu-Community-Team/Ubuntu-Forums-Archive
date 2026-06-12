---
title: "Is there a USB live version with no install option ?"
date: 2016-05-01
forum: General Help
---

### Post by mangurian2 on 2016-05-01
I want my kids to use a USB stick to run ubuntu.  I am afraid they will accidentally choose the option to install ubuntu instead of try ubuntu.
Is there a USB version without the install option ?

---

### Post by RobGoss on 2016-05-01
If there is I have not seen it yet, Have you try deleting it from the Live disk...

---

### Post by jeremy31 on 2016-05-01
I think it is possible to install Ubuntu to a thumb drive if it is large enough, bootloader and all.  Then you can go into BIOS and set the boot order to prefer the USB over HDD and it should boot to USB when it is present.  It is likely more secure than a live version with no sudo password

---

### Post by mangurian2 on 2016-05-01
Can anyone tell me what I can edit on an Ubuntu Live USB stick to disable the "INSTALL" Ubuntu option at startup?
That would leave only the option to run Live from the USB stick.

Thanks for any help,

---

### Post by lisati on 2016-05-01
Installing to a USB stick should do the trick.

---

### Post by yancek on 2016-05-01
An installation of any Linux system as a "live" install is a read-only system and no changes are saved on reboot.  You can do an actual install of Ubuntu to a flash drive if it is at least 8GB.  With this option you will not have the installer.  Or if you have persistence enabled you might be able to remove the "ubiquity installer" per instructions at the site below.

[http://askubuntu.com/questions/286017/how-can-i-remove-install-this-from-my-ubuntu-usb-installation](http://askubuntu.com/questions/286017/how-can-i-remove-install-this-from-my-ubuntu-usb-installation)

---

### Post by mangurian2 on 2016-05-01
But would that require a dual boot startup?   I don't want to mess with my boot.

---

