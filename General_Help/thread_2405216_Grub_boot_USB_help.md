---
title: "Grub boot USB help"
date: 2018-11-03
forum: General Help
---

### Post by confrontation2 on 2018-11-03
Trying to boot USB via GRUB to install Windows 10 or install Windows 10 via boot USB from GRUB 2, whichever makes better sense. I'm using Ubuntu 18.10.

I have tried

set root=(hd0,1)
chainloader +1
But I get the "error Invalid EFI file path" response.

I have also tried

set root=(hd0,1)
chainloader (hd0,1)+1
But get the same error.

I know GRUB sees my USB and I have seen a list from the USB as to what files and folders are on the USB, I just can’t seem to get it to boot.

Edit: also I can not boot in to bios/uefi as it is password protected and I have no way to get the password. I can also boot Linux from USB but Windows will not boot with either MBR or GPT.

Any ideas would be great.

---

### Post by yancek on 2018-11-03
If you are trying to boot windows extracted to a usb from an installed Ubuntu with Grub, it is not likely it will show as (hd0,1).  What you need to do is to boot Ubuntu with your windows flash drive attached and run:  sudo blkid to get the UUID for the windows partition on the usb.  Then use the UUID in the menuentry rather than a Grub drive/partition entry such as (hd0,1).  The sample entry below worked for me on my system, simply replace the UUID shown below with the one you get from the blkid command.  You can put this entry in your Ubuntu grub.cfg file and use it if you do NOT update-grub or you can do it from the menu on boot.

> menuentry "Start Windows Installation" {
 insmod ntfs
 search --no-floppy --fs-uuid 770E690217836CBB --set root 
 chainloader +1 
 boot
}

The entries you posted are looking for windows EFI files on your installed system with an EFI partition and that won't work.

---

### Post by oldfred on 2018-11-03
Is system UEFI?
Normally you directly boot install media from UEFI/BIOS.
UEFI directly boots Windows from /EFI/Boot/bootx64.efi on USB. (same as Ubuntu installer, but different bootx64.efi).

---

### Post by sudodus on 2018-11-03
You can try to make a **Windows installer USB pendrive** with mkusb according to the following links,

[mkusb](https://help.ubuntu.com/community/mkusb)

[Windows USB install drive](https://help.ubuntu.com/community/mkusb#Windows_USB_install_drive)

---

