---
title: "Grub cant detect USB"
date: 2017-04-24
forum: General Help
---

### Post by movesp on 2017-04-24
Hi,
i'm running a basic Ubuntu 17.04 server install on a virtualbox.  For learning purpose i want to copy some linux images to a usb and boot  from it via the Grub command line by selecting the approriate kernel on  the usb.
After booting the system and stopping at grub, I enter the command line by pressing "c" and type "ls" but I only get:
```
(proc) (hd0) (hd0,msdos1)
```

How  has the usb to be prepared? I often read articles where they dd'ed the  image directly to /dev/sdX. I always thought this would be for partition  tables only and filesystem would be on /dev/sdx1, /dev/sdx2 etc.
I  tried to delete all partitions with fdisk and created 1 primary  partition with default values. After that i used mkfs to create a ext2  filesystem on /dev/sdx1.
Then I dd'ed the image to the usb.

How can I get my USB recognized by grub?

---

### Post by ajgreeny on 2017-04-24
Perhaps these pages will possibly help you to do what you want, if I have understood you properly.
[https://ubuntuforums.org/showthread.php?t=1288604](https://ubuntuforums.org/showthread.php?t=1288604)
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

You need to install grub to the USB as far as I'm aware, for the second of those two links, though it is a long time since I have used a usb in this manner.  I have never used the second method of using the hard disk's grub to boot an .iso file but it looks as if that should be similarly possible.

---

### Post by movesp on 2017-04-29
Mh but i have already installed Grub with my Ubuntu install.
I just want to boot a linux dristribution from an usb device with it.

I press "ESC" while in Grub and "c" to get to the command line. But after entering "ls -l" i only see
```
(hd0) (hd0, msdos1)
```
which is my virtualbox disk where Ubuntu is installed on.

The exact command to get the distro image on my usb was:
```
**[FONT=courier new]sudo dd if=~/Desktop/reactos.iso of=/dev/sdb oflag=direct  bs=1048576[/FONT]**
```

I also formatted the usb under Windows 7 with FAT to test if Grub recognizes it, but same problem after typing "ls -l".
Is this a Virtualbox problem? When booting to Ubuntu i can use the usb.

---

### Post by yancek on 2017-04-29
I've never tried booting another OS on a flash drive from a VirtualBox install so I'm not sure if it would work or how if it does.  The Grub output is because it only sees one bootable device, the Ubuntu in VBox.  In VirtualBox under Settings, there are options under USB which you might take a look at.  It is certainly possible to boot a system on a usb drive in VirtualBox if it has a bootloader but I'm not sure that you can boot the Ubuntu in VBox and select a system on a usb drive.  This is quite simple to do on actual hardware so I would expect it is the way VirtualBox works.  You might check the Settings/USB in VirtualBox or the VirtualBox documentation at their site.

---

### Post by movesp on 2017-04-29
> It is certainly possible to boot a system on a usb drive in VirtualBox if it has a bootloader but
What do you mean by that? I have and use the bootloader which comes with the default Ubuntu installation installed on my VM disk (not USB).
With the dd command in my reply i copy the image to USB. Does the USB then automatically have a bootloader?
I thought i can load up the VM, stop at Grub2, select the proper kernel on the USB with the Grub2 command line and boot. Is this correct? Would this work on normal system?

I already checked the USB setting but nothing changed. Since the VM is already at Grub2 bootloader point what difference is there to a physical system?

---

