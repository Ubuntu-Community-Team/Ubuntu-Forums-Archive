---
title: "Can't boot back into Windows 8 and trobule with Ubuntu booting"
date: 2015-05-26
forum: General Help
---

### Post by alexmk100 on 2015-05-26
I just installed Unbutu on my computer and I can get onto Unbutu by jumping through a few hoops while starting up my computer however I can't get back into windows. I ran boot repair and this is what it gave me as a link to post in forums. Please help!!
[http://paste.ubuntu.com/11364983/](http://paste.ubuntu.com/11364983/)

---

### Post by Bucky Ball on 2015-05-26
Welcome. Looks like you did a Wubi install. Just to say that Wubi is no longer supported by Canonical and there is little help to be found here for it. I would suggest installing a regular dual-boot, Win and Ubuntu on separate partitions, but hopefully we can get you out of this first ...

---

### Post by alexmk100 on 2015-05-26
Hi Bucky Ball, okay thank you for your help. I am very new to linux (downloaded last night) and I am totally lost. Do you have any advice on where to go from where I am at? I am currently using Ubuntu right now but I still can't get into windows at all. I tired using the windows 8 disk to recover but it said that it could not identify the partition to recover or that the partition was locked.

---

### Post by grahammechanical on 2015-05-26
We do need to be clear on your set up otherwise we give inaccurate advice. I am guessing correctly? First hard disk (sda) with Windows 8 with a Wubi install of Ubuntu. But do you also have a second hard disk (sdb) with Windows 8 and a dual boot of Ubuntu 15.04?

You did not allow Boot Repair to do any repair. It is good to seek advice first. You need to get into Windows 8 on the first hard disk (sda) and remove that Wubi install of Ubuntu. I do not know how to do that. Through Add/Remove programs? Wubi is not compatible with Windows 8.

For a dual boot installation of Ubuntu with Windows 8 we need to follow the guide lines here:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Does the motherboard have a BIOS or UEFI boot system? Also, what hard disk is the motherboard booting from? If you can set it to sdb you might load Windows.

Regards.

---

### Post by oldfred on 2015-05-26
Both drives are MBR(msdos) so installs are BIOS not UEFI.

Do not run Boot-Repairs auto fix. But do use advanced mode and select Windows and install Windows boot loader to sda, and select Ubuntu and install grub to sdb.
Then from BIOS you should be able to directly boot sda drive.
And if you boot sdb then you should be able to boot Ubuntu.

Only if you have Windows 8 fast startup or always on hibernation off, will you be able to add Windows to grub menu and boot it from that. This will find & add Windows once you have Windows settings correct.
sudo update-grub

 Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

