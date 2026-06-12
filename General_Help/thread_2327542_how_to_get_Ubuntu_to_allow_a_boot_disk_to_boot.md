---
title: "how to get Ubuntu to allow a boot disk to boot"
date: 2016-06-12
forum: General Help
---

### Post by wheelie207 on 2016-06-12
I have 3 computers and they run Ubuntu with different setups. Now I want to put a different distro on one of the computers, but when I try to boot from a DVD or a USB stick they end up not booting, a grub screen comes up with boot to Ubuntu , Ubuntu advance option and setup.
It shows nothing of the DVD or usb stick with the distro.
My computer shows that Ubuntu was installed using UEFI or something to that affect. How can I get my DVD or usb stick to be recognized and boot from them without the grub screen from popping up. Thanks

---

### Post by yancek on 2016-06-12
If you  are trying to boot a DVD or flash drive and are getting the boot menu from the hard drive that means you have not changed the boot priority in the BIOS of your computer.  You need to do that.  Check the manual that came with the system or do an online search for the specific computer you have.  You could also post that info here and someone may be familiar with it.  Which other operating system are you trying to install?  You will need to boot and install it UEFI also or one of the systems will not boot.

---

### Post by wheelie207 on 2016-06-12
I forgot to mention that I have the BIOS settings so it is CD/DVD first, usb drive/or stick second and third is internal hard drive.
Also I am trying to install debian 8.5 so I can mess around with Linux from scratch.

---

### Post by Bucky Ball on 2016-06-12
You don't need to install Debian to play with LFS. If you want to play around with LFS, you can do so starting from [here]("http://www.linuxfromscratch.org/lfs/view/stable/chapter02/creatingpartition.html") or starting from the beginning of that book. You need a blank partition to start with. 

If you're after help installing Debian, this is not the place to post for it. You'll improve your chances by posting in a Debian forum. We have [a sub-forum for Debian]("http://ubuntuforums.org/forumdisplay.php?f=161") but the specialised support sections here deal with Ubuntu and its flavours.

Good luck.

---

### Post by grahammechanical on 2016-06-12
It is not only the boot priority that needs to be set. On my BIOS boot system under Boot settings where I change boot priority I also go to Hard drives and choose which drive to load from. That is what I go to get my machine loading from a USB memory stick or DVD.

The USB stick needs to be in the USB port for the system to detect and present it as an offering to load from.

Regards

---

### Post by wheelie207 on 2016-06-12
I don't want to have Ubuntu to build a LFS. I would rather use debian.
Also my bios is setup correctly and it is Ubuntu that is preventing my DVD from booting.

---

### Post by X-RED_Tech on 2016-06-12
No, booting from an installation media happens before Ubuntu or any other installed OS.
It depends on BIOS/UEFI and the installation media. Often preferable to use the one-time boot key if available just to be sure it is booting (or trying to boot) from the optical drive.
If the media or the drive itself are faulty it will default to the next boot device in order. That is what's giving you the impression Ubuntu has something to do with it.

---

