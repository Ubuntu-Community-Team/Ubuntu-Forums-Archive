---
title: "Startup disk creator unable to select Windows ISO"
date: 2022-01-12
forum: General Help
---

### Post by satimis on 2022-01-12
Hi all,

Ubuntu 20.04

Something strange happens here.  Startup disk creator can't select all Windows ISO but can select Linux ISO.

I have tried both my daily working PC and my spare PC.  It is the same.  It worked last week.  I don't know WHY?

Please help how to fix the problem.  Thanks

Regards

---

### Post by KBar on 2022-01-12
Mandela effect.

It has never been able to write Windows images to a USB drive. That's because Windows disk images are structured differently.

---

### Post by satimis on 2022-01-12
> **KBar said:**
> Mandela effect.

It has never been able to write Windows images to a USB drive. That's because Windows disk images are structured differently.
Yes, according to my recollection.  It worked for me before.

Last week I have created a Windows 10 boot USB.  I'm not quite sure whether running Ubuntu 20.04 or running Linuxmint 11.2.  That Win 10 boot disk was later wiped out installing Ubuntu 20.04 boot USB.  I'll try again on Linuxmint 11.2 later.

Regards

---

### Post by sudodus on 2022-01-12
When running Ubuntu, you can use [mkusb](https://help.ubuntu.com/community/mkusb) or [woeusb](https://askubuntu.com/questions/1097560/woeusb-error-code-256-with-ntfs-formatted-usb/1098185#1098185) to create a Windows installer USB drive from a Windows iso file.

[hr][/hr]
The Ubuntu Startup Disk Creator is a cloning tool, and cloning does not make a bootable drive from a Windows iso file.

---

### Post by satimis on 2022-01-12
> **sudodus said:**
> When running Ubuntu, you can use [mkusb](https://help.ubuntu.com/community/mkusb) or [woeusb](https://askubuntu.com/questions/1097560/woeusb-error-code-256-with-ntfs-formatted-usb/1098185#1098185) to create a Windows installer USB drive from a Windows iso file.

[hr][/hr]
The Ubuntu Startup Disk Creator is a cloning tool, and cloning does not make a bootable drive from a Windows iso file.

Hi,

Thanks for your advice.

I already have Windows 10 boot USB stick created by referring to following document:-

How to Easily Create Windows 10 Bootable USB on Ubuntu or Any Linux Distro
[https://www.linuxbabe.com/ubuntu/easily-create-windows-10-bootable-usb-ubuntu](https://www.linuxbabe.com/ubuntu/easily-create-windows-10-bootable-usb-ubuntu)

Steps performed as follow;

Start gparted

GParted -> Devices
select /dev/sdf

right click /dev/sdf1 -> umount
(screenshot_01.png)

Again
Device -> Create partition table on /dev/sdf -> Apply
-> select new partition table type: [gpt]
(screenshot_02.png)

-> right-click "unallocated space" -> select New to create new partition -> Add
(screenshot_03.png)

Closed gparted

Right-click Windows 10 IS0 -> select "start Open with image disk mounter"

Drag&Drop all files on USB stick
(screenshot_04.png)

Remark: It'll take some time to finish.

Now I have a Windows 10 USB installer.

Also I have installed Windows 10 on a bland-new 1TB SATA3 6G/s SSD to begin my adventure running Video Editing Software on bare-metal Windows 10.

Thanks

Regards

---

### Post by KBar on 2022-01-12
As you may have already noticed, the program you used is called **GParted** which is not at all **Startup Disk Creator**.

But I'm glad that you could solve this on your own.

---

