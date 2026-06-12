---
title: "[SOLVED] Can't Start Windows Without Ubuntu Drive"
date: 2008-02-20
forum: General Help
---

### Post by tomihasa on 2008-02-20
After installing Ubuntu 7.10 to my HP laptop having Windows XP in it, I haven't been able to start Windows XP without my external USB hard disk. This is the text I get when I don't have my USB disk connected to my laptop:

```

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 21

```

I mainly use Windows XP, so how can make Windows XP start as a default or maybe see a screen where to select the operating system I want to start?

---

### Post by danwood76 on 2008-02-20
To load linux (and windows for that matter) you need to have a boot loader.

Ubuntu uses grub as the boot loader and stores information in the /boot folder.
This will be stored on your ubuntu drive and so its giving you this error.

What you can do is install grub to a small boot partition on your XP drive, this would then make it possible to load grub and have that to choose between the two OS's without needing the ubunth HD.

Another alternative, if your motherboard allows booting off of USB drives is to reinstall grub to the MBR of your external hard disk and reinstall the XP bootloader to the MBR of your XP disk.
Then choose the boot priority so that if the drive is plugged in it loads from that first, otherwise it goes to the hard disk.

---

### Post by Perpetual on 2008-02-20
I am at work and can't dig into this but to give you something to look for... I believe you must have installed grub on the USB and now when the computer boots it is failing to initialize grub.

Have a read through [this thread]("http://ubuntuforums.org/showthread.php?t=659068").

---

### Post by ajgreeny on 2008-02-20
If ubuntu is on the external disk and you put grub onto the MBR of the windows disk (the internal laptop disk) the reason is simply that grub runs but can't find the /boot/grub/menu.lst file because it is on the external disk.  The best way round this is to run ubuntu, and from that install grub onto the external disk itself with ```
sudo grub-install /dev/sda
```though you may need to change the sda to whatever the disk is seen as by ubuntu.  Check that with ```
mount
``` when ubuntu is running.  The top entry should be /dev/sda1 or something similar so use that /dev name without the number part.

You will now need to restore the windows XP MBR by booting your windows install CD and going to the recovery module, and running **fixmbr**.  Ignore the warnings about possible problems of doing this and continue to restore and then in BIOS set to boot from external disk first, then internal disk second.  Now when the external disk is missing the system will default to the internal disk and windows will boot normally, but when the external is plugged in you should get a grub menu and can then choose which OS to use.

---

### Post by tomihasa on 2008-02-22
I made the easy(?) solution and re-installed both Windows XP and Ubuntu 7.10 to my internal hard drive. Now I need to download and install some software and updates for Windows... :)

---

