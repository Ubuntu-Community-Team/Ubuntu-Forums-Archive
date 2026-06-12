---
title: "questions regarding persistent USB install"
date: 2017-06-10
forum: General Help
---

### Post by ardouronerous on 2017-06-10
I want to create a persistent USB install of Lubuntu 16.04

1. What is the difference in performance between a LiveUSB and a persistent USB install of Lubuntu?

2. My laptop can boot off a LiveUSB, would that mean it could also boot off a persistent USB?

3. I heard that creating a persistent USB install is bad idea because it will break the USB, is that true?

4. What brand of USB would you recommend I use for creating a persistent USB?

5. How much GB is recommended for persistent USB?

---

### Post by dragonfly41 on 2017-06-10
Here is my profile on an ageing Dell laptop.

I keep a persistent LiveUSB in reserve to be used only when needed (data recovery etc.). This is an 8 GB device but it could be less.

Then I have an internal hard drive on which I have partitioned several OS versions (dual boot windows and Ubuntu earlier 14.04 32 bits).

And finally I have a recycled external 500 GB drive (in a container) where I have installed Ubuntu 16.04 (64 bits) for migrating from 14.04 (32 bits) to 16.04 (64 bits).  Indeed that is what I'm using right now. My laptop monitor is dead so I'm on a second monitor.   Time to buy a new PC. A tower PC since it is easier to get inside.

..

Your Q1.
I don't really worry too much about LiveUSB performance since I don't expect to use LiveUSB for intensive work. It is slower but it is not in daily use.

Your Q2.
Yes.

Your Q3.
I have not experienced that but I guess over thrashing might do that.

Your Q4.
Brand is not important.

Your Q5.
Varies. I use an 8GB device.

---

### Post by kurt18947 on 2017-06-10
Apologies for an early thread hijack:redface:.  If your objective is to try Ubuntu without making a significant committment, have you considered creating a full install on a USB drive? Advantages of a full install over a live USB with persistence:

1) It can be updated just like being installed on a hard drive. A persistent install cannot.

2) Any device drives such as from AMD/ATI or Nvidia can be installed and will persist. I'm not certain the same is true of persistent Live USB installs, it may be.

3) Storage is limited on persistent USB drives. I think the limit is 4 GB. Storage on a full USB install is limited only by the size of the flash drive.

4) Booting from a full Flash drive install is slower than from a hard drive though it's not bad, perhaps a minute.

If you choose to go this route, I'd recommend unplugging/removing your hard drive prior to installing. It's easy for GRUB to be installed in the wrong place. If your hard drive is not accessible, it's not going to be messed up/become unbootable.  I use the advanced option in the installer and don't create a swap partition. If I needed swap due to low RAM, I'd create a swap **file.**

Possible downsides of a full flash drive install (that I can think of)

1) I don't know that a full install can be used to rescue/repair another operating system on another partition like a live USB can.

2) It's going to be somewhat slower to boot and launch new applications

3) Flash drives do wear so eventually a flash drive install is going to fail and sooner than a hard drive or SSD install.

  I use a 32 GB. flash drive (16 GB. would probably be enough) and prefer those without added extras. I've had good luck with Sandisk or MicroCenter store brand devices.

I'm certain others more knowledgeable will check in.

---

### Post by C.S.Cameron on 2017-06-10
1) Performance between Live USB and Persistent USB is almost identical except a Live USB boots considerably faster.

2) Yes, everything else being equal, A persistent drive made using a different method than the Live drive may have a slightly different performance.

3) A decent USB is good for at least 10000 writes and has wear leveling. For a 32GB USB3 drive: 32GB x 10000 / 0.05GB/s = 222 full 24h days, (possibly many years of actual use).

4) USB3 and faster the better, see Google for actual benchmarks.

5) What is the persistent drive being used for? If to power a Kodi machine or control a remote IP camera, perhaps 4GB is enough, if it is being used as a desktop replacement then estimate the volume required for your programs, home can be put on it's own partition, (home-rw), and data can be stored on a Windows friendly NTFS partition.

My favorate USB drive maker is **mkusb**.

---

### Post by monkeybrain20122 on 2017-06-10
> **kurt18947 said:**
> 

If you choose to go this route, I'd recommend unplugging/removing your hard drive prior to installing. It's easy for GRUB to be installed in the wrong place. If your hard drive is not accessible, it's not going to be messed up/become unbootable.  I use the advanced option in the installer and don't create a swap partition. If I needed swap due to low RAM, I'd create a swap **file.** 

I have made many full installations in external hard drives and usb drives. I never removed the internal hard drive. For me it is a big headache to open the laptops and keep track of all the loose screws and some laptops are not so easy to open because of old worn out screws or strange security screws like I have on this Toshiba laptop (still looking for a screw driver :) )

To avoid the danger that you mentioned, I recommend doing manual install (advanced option) instead of automatic and there are other advantages too like you can have separate / and /home and not having a useless /boot partition which often causes troubles after many kernel upgrades if people forget to run autoremove regularly(run out of space) 


**@OP**. if you do manual install you will see the partition table after you choose your time and date and keyboard settings, at the bottom there is a box to choose where to install grub. Choose the external hard drive (/dev/sdc typically, though not always : /dev/sda would be your internal hd, /dev/sdb would be your live usb from which you run the installer, but check carefully first) Also performance is a lot better on an external hdd than an usb flash and it doesn't have anything to do with size. A 6 G SATA hdd from a very old laptop performs a lot better than a 16G flash. I have done this many times, except for boot time performance for a full install in an external SATA is almost identical to internal installation even with only usb2 connection. In a flash drive it is slow and not really usable except as a demo. So go for external hd if you have one laying around.

> 

1) I don't know that a full install can be used to rescue/repair another operating system on another partition like a live USB can.


I'm certain others more knowledgeable will check in.

No reason why not. You just need to install gparted and whatever rescue/repair software that you need to run off a Ubuntu live usb.

---

### Post by kurt18947 on 2017-06-10
> **monkeybrain20122 said:**
> I have made many full installations in external hard drives and usb drives. I never removed the internal hard drive. For me it is a big headache to open the laptops and keep track of all the loose screws and some laptops are not so easy to open because of old worn out screws or strange security screws like I have on this Toshiba laptop (still looking for a screw driver :) )



Valid point. I'm spoiled by having 'typical' Thinkpads where the hard drive removal consists of removing one Phillips screw. Some machines, particularly the ultralights make hard drive removal nearly impossible for normal users.

---

### Post by C.S.Cameron on 2017-06-11
One nice thing about leaving your HDD in place while installing to flash drive, (as long as you don't overwrite it or put grub in the wrong place, etc, etc), is that the internal HDD is added to the Flash drives grub menu so that there is no need to remove the flash drive when booting the internal drive.

---

