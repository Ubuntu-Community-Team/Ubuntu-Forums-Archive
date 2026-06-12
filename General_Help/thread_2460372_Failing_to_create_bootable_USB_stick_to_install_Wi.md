---
title: "Failing to create bootable USB stick to install Windows"
date: 2021-04-08
forum: General Help
---

### Post by titania177 on 2021-04-08
Hi, I'd welcome any help please! I have a new-ish Lenovo Thinkpad x1 and I'm having hardware issues on it (part of the trackpad isn't working and the 'G' key sticks) . The technical support at Lenovo say they can't help because I installed Ubuntu over Windows (I bought this laptop because it was recommended as being a good one to run Ubuntu on). They want me to reinstall Windows to check that the problems are definitely hardware- and not software-related. So I have been desperately trying to create a working bootable USB key to install Windows 10 from. I've downloaded the ISO image file for the 64-bit version of Windows 10 from Microsoft, used UNetbootin to create the bootable USB stick, checked that it's top of the boot order in the BIOS. When I restart the computer, it starts booting from the USB stick - and then says it can't find the .wim file and aborts the installation. I formatted the USB stick as FAT, as recommended, is it something to do with the fact that the ISO file  for the 64-bit version of Windows 10 is larger than 4GB?  Please help! I'm not extremely techy, but can follow commands in the Terminal window if necessary.

---

### Post by yancek on 2021-04-08
> The technical support at Lenovo say they can't help because I installed Ubuntu over Windows 

That would be the only (or at least most important reason) to leave windows on a computer with it preinstalled.  It's the same for all manufacturers as far as I know and always has been.

Unetbootin is designed to create Linux bootable usb drives so it won't work with windows.  If the .wim file is over 4GB, you will need to use an ntfs filesystem.  The link below explains one method of doing this from Ubuntu.  It also explains a method of doing it by creating an ntfs partition on your hard drive. 

 [https://www.linuxbabe.com/ubuntu/easily-create-windows-10-bootable-usb-ubuntu](https://www.linuxbabe.com/ubuntu/easily-create-windows-10-bootable-usb-ubuntu)

---

### Post by titania177 on 2021-04-08
Thank you so much! I'd read lots of articles trying to figure this out but none of them explained this as clearly and succinctly as you!

---

