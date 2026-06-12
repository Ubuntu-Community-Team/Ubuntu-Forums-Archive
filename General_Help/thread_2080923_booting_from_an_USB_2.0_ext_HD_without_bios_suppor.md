---
title: "booting from an USB 2.0 ext HD without bios support"
date: 2012-11-05
forum: General Help
---

### Post by maskiepop on 2012-11-05
I have installed xubuntu 12.04 in an 60 G USB 2.0 external HD. My problem is that I oftentimes find myself in a situation where the the PCs or laptops available to me do not support booting from an USB device; their biosses do not cater for it. 

I have seen a number of write-ups concerning this:

[https://help.ubuntu.com/community/BootFromUSB]("https://help.ubuntu.com/community/BootFromUSB")

[http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-11-10/]("http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-11-10/")


I think these will solve my problem except for one small hitch: my installed xubuntu boots up using GRUB2; the two articles above are talking about GRUB.

I cannot use these unless these are modified for GRUB2, I think. Can someone show me how the above might be modified for my GRUB2/xubuntu installation?

I'd appreciate that very much.

Thx,

m

---

### Post by dino99 on 2012-11-05
if that extern hdd has the OS +grub2 installed on it, then no needs to worry about something else, but the host bios need to be able to boot on usb device, otherwise no way, thats simple.

---

### Post by maskiepop on 2012-11-05
> **dino99 said:**
> ... but the host bios need to be able to boot on usb device, otherwise no way, thats simple.

dino99, 

The Intro to the Ubuntu Community write up says precisely that it can be done even if there is no bios support. And then it describes two methods, one of which involved a "custom" GRUB boot cd.

But thanks for what you suggested. I will proceed to build a boot cd from GRUB.

m

---

