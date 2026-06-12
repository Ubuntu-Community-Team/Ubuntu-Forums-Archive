---
title: "Multi OS bootdisk with grub?"
date: 2015-07-30
forum: General Help
---

### Post by Colo2 on 2015-07-30
This may be a strange request.

I have a 32GB USB Stick, and I want to use it as a boot disk for multiple OS.

The idea is when booting from this USB stick, I am presented with GRUB, or another likeness to be able to scroll through a list and select from multiple operating systems. To then boot into liveUSB, Windows etc.. - 

Is this possible?

Thanks

Tom

---

### Post by Colo2 on 2015-07-30
I just realised this may not have been the best place to post this, if it isn't, sorry.

---

### Post by jeffa2 on 2015-07-30
> **Colo2 said:**
> This may be a strange request.

I have a 32GB USB Stick, and I want to use it as a boot disk for multiple OS.

The idea is when booting from this USB stick, I am presented with GRUB, or another likeness to be able to scroll through a list and select from multiple operating systems. To then boot into liveUSB, Windows etc.. - 

Is this possible?

Thanks

Tom
[h=1][/h]

Have you tried the[ YUMI – Multiboot USB Creator]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/")?

---

### Post by Colo2 on 2015-07-30
that looks interesting thanks :) do you know if you can install windows on it too?

---

### Post by yancek on 2015-07-30
Based on the quote below from the YUMI site, I would say no to installing windows.

>  YUMI was intended to be used to try to run various "LIVE Linux" Operating Systems from USB

Also, if you try to install windows on a usb drive, you will probably see the following message.  At least I did when I tried to install windows 10 on one.

> windows setup does not support configuration or installation to a disk connected through usb or IEEE 1394 ports

I had a 16GB flash drive on which I put 26 Linux Live systems so the number of Linux distributions you can put on a drive is limited only by the size of the drive.  Are you planning to only put Live images on it or actually install one or more and do you want to just boot from the flash drive or access installed systems on another hard drive or hard drives?

---

### Post by oldfred on 2015-07-30
You can add the typical chain load entry to boot Windows on hard drive. And with some work you can get grub to chain boot a Windows repair flash drive and other Linux live installers/repairCD as ISO using grub2's loopmount.

But now older systems are BIOS and newer are UEFI. And once you start booting in one mode you cannot switch to another boot mode. So if you have grub installed in UEFI mode it can only boot other UEFI systems. Or if grub is on BIOS boot drive then it will only boot other BIOS based systems.

---

