---
title: "Ubuntu LIVE USB problem"
date: 2019-02-08
forum: General Help
---

### Post by chris420 on 2019-02-08
Hi all,


I've made a LIVE USB of Ubuntu Studio 16.04. I want to use this to boot on machines from a USB so I don't need to install Ubuntu onto the machine's hard drive. I've given the USB stick 8 Gb for file preserving. I've also put a little script on the stick that loads QjackCtl from start up. 


All works fine for a couple of weeks and the system can be booted from USB on many machines without problems. 


However, after a couple of weeks (or multiple booting) the USB image slowly stops working, QjackCtl may just crash and things stop working on the USB system. These problems don't seem to transpire to a hard drive installation. I know a USB stick data transfer is less than a hard drive (although I am using USB 3.0). Are there any other reasons why this USB system slowly dies or is it just down to slower data transfer rates on USB 3.0 sticks compared to hard drives? 


Thank you in advance

---

### Post by yancek on 2019-02-08
It might just be wearing out.  Nothing lasts forever and sometimes, the same usb from the same manufacturer will not last nearly as long as another similar one.  Same applies to a lot of products.  If your ports on the machine are 2.0, it doesn't matter if the usb is 3.0.  No other ideas.  Good luck.

---

### Post by C.S.Cameron on 2019-02-08
If you want a USB drive that is more stable than a persistent system try doing a Full install to USB.
The longest I have had a Persistent drive work is three months, I replaced it with a Full install and it is still working three years later.
It is also faster, updatable and upgradeable.

---

### Post by chris420 on 2019-02-20
Ah thanks for that. Would the full install also work on many another machines? ie. would it install drivers for many different graphics cards and sound cards on the fly if you USB was inserted into many different machines?

---

### Post by C.S.Cameron on 2019-02-20
A full install has all the stuff a persistent install has except GParted and Ubuntu installer. As long as you don't install proprietary drivers it should work on the same computers a Persistent install works on. Nowadays Nvidia graphics checks if the computer has a Nvidia card before loading at startup.
For a full install USB I start with a mkusb install to insure BIOS and UEFI compatibility. [https://askubuntu.com/questions/873004/ubuntu-on-a-usb-stick-boot-in-both-bios-and-uefi-modes/1118412#1118412](https://askubuntu.com/questions/873004/ubuntu-on-a-usb-stick-boot-in-both-bios-and-uefi-modes/1118412#1118412)

---

