---
title: "Ubuntu 14.04 grub rescue fix"
date: 2015-01-02
forum: General Help
---

### Post by johan19 on 2015-01-02
I have a dual boot system with Vista and Ubuntu.
Had a sudden issue where machine complained about Intel ME error - and after that machine did not boot and only displayed grub rescue.
I tried running boot-repair , but got several errors : could not delete files etc...
I created a Live CD on a USB stick and booted on that.
([COLOR=#545454][FONT=Helvetica]www.ubuntu.com/download/ubuntu/download)
[/FONT][/COLOR]
Then I ran :

sudo mount /dev/sdb5 /mnt  

I determined the the actual disk to mount by running sudo fdisk -l

Then ran:
sudo grub-install /dev/sdb --boot-directory=/mnt
(Only refer to disk and not actual partition)


Other posts refer to --root-directory - and that is **wrong **- took me a while to find the correct one which is boot-directory for 14.04

When I then rebooted I got the grub interface and not grub rescue anymore - which is an improvement.

I then created a boot-repair usb stick, and booted with that one.
([COLOR=#333333][FONT=Ubuntu]The easiest way to use Boot-Repair is to create a disk containing the tool (eg [/FONT][/COLOR][Boot-Repair-Disk]("http://sourceforge.net/p/boot-repair-cd/home")[COLOR=#333333][FONT=Ubuntu], a disk starting Boot-Repair automatically), and boot on it.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Remark : it is recommended to install the ISO on a [live-USB]("https://help.ubuntu.com/community/Installation/FromUSBStick") (eg via [UnetBootin]("http://unetbootin.sourceforge.net/") or [LiliUSB]("http://www.linuxliveusb.com/") or [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")). Do not burn it on a DVD if your computer has Windows8 pre-installed, or if your boot is in [EFI]("https://help.ubuntu.com/community/EFI") mode.)
[http://sourceforge.net/projects/boot-repair-cd/?source=typ_redirect](http://sourceforge.net/projects/boot-repair-cd/?source=typ_redirect)

[/FONT][/COLOR]

I then ran the boot-repair, and after that finished was able to boot and get the boot options to boot to either Windows or Ubuntu again.

---

