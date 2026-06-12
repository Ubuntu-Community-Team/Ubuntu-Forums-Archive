---
title: "Technogym Cross trainer running Ubuntu V1.13.3"
date: 2023-01-13
forum: General Help
---

### Post by sparkyv860 on 2023-01-13
Hello, I am hoping someone can help me. I know nothing about Ubuntu or programing. I purchased a Technogym Cross Trainer which is running Ubuntu V1.13.3. It is failing to load up and run and I cannot seem to find where to get help to fix my problem without spening hundreds of $£. 

I have managed to get a keyboard connected to it and I think i need to perform a system check of the boot partition but I dont know what commands to enter to sort this issue out. I also dont have the original software on a USB stick or know where to get it from, as I understand you can boot from that? 

The message I am getting is > No init found. Try passing init= bootarag. I have attached screen shots of the machine and would really appreciate some help. Many thanks, Mark. :)

---

### Post by ActionParsnip on 2023-01-13
[https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-rescue-a-non-booting-grub-2-on-linux#:~:text=Booting%20From%20grub%3E&text=The%20first%20line%20sets%20the,location%20of%20the%20root%20filesystem](https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-rescue-a-non-booting-grub-2-on-linux#:~:text=Booting%20From%20grub%3E&text=The%20first%20line%20sets%20the,location%20of%20the%20root%20filesystem).

---

### Post by Topsiho on 2023-01-15
I think you should get back to the producer of your trainer, as I'm afraid no one here can answer your question. The Ubuntu version you mention  never existed, as all Ubuntu versions are named after another scheme: year.month and a .number eventually, such as Ubuntu 22.04.1 (the newest version)
The LTS (long time support) versions are supported 3, 5 or longer years, and after that they don't work and should be replaced by a newer one, which you can download and install (on a computer) for free. Choose an LTS--version, 20.4 or  22.4.
As your trainer is not an (ordinary) computer I think you should get back to the manufacturer or where you purchased it from. Probably the manufacturer used a modified version of some version of some Ubuntu?

I hope you 'll be training soon again :)   I  have a rowing machine

Topsiho

---

### Post by Topsiho on 2023-01-15
I have been thinking :)

I have looked into the repositories of ubuntu for the file init and saw that one of the files is for busybox with exactly the number you mentioned!
So what you could do is download (somehow, maybe someone here can tell you how) init and the files associated with it, which you could put on an usb-stick which you could put into your trainer. That's what I would try to  do.
So that the trainer could find it while started.

BTW why don't you start running? In the wild, free and easy? Dry and wet weather, adventurously?
I did that for 40+ years and enjoyed that marvelously.

Topsiho

---

### Post by guiverc on 2023-01-15
Your Ubuntu system is really old, and is **not** a *supported* system.

You can refer to this page to see *supported* versions of busybox (*what you read as Ubuntu version but were incorrect, you're seeing `busybox` as Ubuntu isn't booting*).

[https://packages.ubuntu.com/search?keywords=busybox&searchon=names&suite=all&section=all](https://packages.ubuntu.com/search?keywords=busybox&searchon=names&suite=all&section=all)

You'll note on that page, the oldest *supported* version of `busybox` (for *standard support*) is 1.27.2-2ubuntu3.4 and not anything with 1.13  (ie. yours is something like [https://launchpad.net/ubuntu/lucid/i386/busybox-initramfs/1:1.13.3-1ubuntu11](https://launchpad.net/ubuntu/lucid/i386/busybox-initramfs/1:1.13.3-1ubuntu11) which you'll note is reported as ***obsolete*** coming from 2010).  It was *supported* until April 2015.

*I'd start with basic hardware evaluation, ie. check the health of your drive(s) using the drive's SMART capacity (I'd boot a live system and check from there; refer [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools) for some details on SMART but we're talking more hardware issues here), maybe also check RAM & of course PSU, as even good components perform badly when fed incorrect power*).

---

### Post by howefield on 2023-01-15
Is this a treadmill of sorts with an attached screen running Ubuntu underneath, yes?

Perhaps the[ manual ]("https://www.technogym.com/vn/download-manuals-and-documents/")has something of value?

---

### Post by Topsiho on 2023-01-15
guiverc is right, busybox on my ubuntu 22.04 system is .30 and not .13, so the numbers are not the same :(

I think the manufacturer is responsible for using such a very obsolete version of Ubuntu. Can't imagine your trainer is that old ...

Topsiho

---

### Post by rc-joe on 2023-11-09
I have a treadmill that has a similar looking bezel that you showed.  Mine is running Ubuntu 12.04.  I'm trying to get it to boot.  Its got a BCM MX2800N motherboard in it.

---

