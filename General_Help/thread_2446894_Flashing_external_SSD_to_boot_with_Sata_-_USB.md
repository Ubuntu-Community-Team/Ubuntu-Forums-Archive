---
title: "Flashing external SSD to boot with Sata - USB"
date: 2020-07-08
forum: General Help
---

### Post by turdbird on 2020-07-08
So I am attempting to make what is commonly referred to as a Live USB drive. However instead of using a USB key i want to be able to use one of my many spare SSD drives. The reasons being, 1 I want to run my raspberry pi off of an SSD drive. Both for reliability and speed. And 2 because I want to have a Live ISO on a different SSD that I plan to use with encrypted persistence.

If I use the "dd" command will it copy the iso into the form of a bootable live OS capable of being booted from a USB - Sata adapter? 

I do know that this is the reason for having a thumb drive with a Live OS on it. However, I want more storage space, and I dont want to pay for a decent sized thumb drive that is USB 3 because they are too costly. I like to use what I've got rather than throw money at things. This is more about wanting to learn than anything. Or I would just stick to my typical thumb drive OS. 

I already have a few VMs on virtualbox as well. 

Thank you in advance. 
Oh and I do not own a Windows machine. So please only give me answers about how to do this on Ubuntu!

---

### Post by dragonfly41 on 2020-07-08
If using Ubuntu I would use mkusb to create your LiveUSB. Beware dd .. having read some recent horror stories of its misuse.
Also research creating a UEFI compatible LiveUSB.  When I created my external Ubuntu on SSD I first went into GParted to create the partitions including an EFI partition (/dev/sdb1) at front of SSD (500 mbits). Then an ext4 partition (/dev/sdb2) for your Ubuntu installation. This added EFI partition (with boot flags set in GParted) allows your SSD to boot without relying on Windows own EFI partition.

---

### Post by tea for one on 2020-07-08
dragonfly41 hit the nail on the head - dd can easily cause untold damage unless you are **very** careful.

If you decide to use dd, make sure that you have **restoreable backups**.

**mkusb** is a far better tool for making live usb or ssd devices (especially with persistent storage).

With a modern motherboard, you should certainly be able to boot an ISO flashed to a ssd in an enclosure.

Also, if your hardware allows, you can install an ISO as a live system on an **internal** ssd (i.e.usb-sata adapter/enclosure not required).

Assuming all OS systems are installed in UEFI mode, then you simply choose your device via the Boot Device function when you power on the PC.

---

### Post by C.S.Cameron on 2020-07-09
Mkusb is the best tool for making a Persistent USB, however I am wondering why you prefer a Persistent USB to a Full install USB?

**Comparison between Persistent and Full install USB**

**Advantages of a persistent install:**

1) You can use the persistent External SSD to install Ubuntu to another computer.

2) A persistent install takes up less space on the External SSD.

3) You can reset the External SSD by overwriting the old casper-rw file with a new one.

4) The Persistent install to External SSD takes less time than a Full install.

**Advantages of a Full install:**

1) You can update and upgrade.

2) If you have problems or wish to modify, the solution is the same as with an internal install, (You can ask for help in these forums).

3) No ugly startup / install screen.

4) Better security, you can use full disk encryption

5) You can use proprietary drivers.

6) Hibernation works.

7) Some persistent installs are limited to a 4GB casper-rw and a 4GB home-rw persistence file, to get more persistence requires persistence partitions. such as mkusb uses. Once casper-rw is full, the drive will not boot.

8) More efficient usage of disk space. Does not require reserved space for persistence.

9) Faster boot, no automatic disk checking or Try Ubuntu/Install Ubuntu screen

Note that once booted, both methods run at about the same speed.

**Full Install Method**

Several methods for creating a Full install USB: [https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)

---

### Post by oldfred on 2020-07-09
Another advantage of a full install, is then you can set up grub to boot many ISO.
I have done that with multiple USB flash drives with BIOS years ago & now with UEFI.
But most of my installs now use same type of grub boot of ISO from one internal drive to install to another internal drive.

Recently got an SATA to USB adapter and found SSD boot to be almost as fast as internal drive. Always thought USB3 port was at least part of reason flash drives were so slow. 

ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by C.S.Cameron on 2020-07-09
Oldfred:

Are you booting the ISO's on the SSD toram?

The 20.04 file system check takes me up to 3 minutes booting USB 2, when I switch toram, it takes 3 seconds.

---

### Post by oldfred on 2020-07-09
I have used the toram parameter for several years as I have 4GB or more of RAM on my systems, except really old 1.5GB RAM laptop, that I really do not use.

But converted to USB3 flash drives even when I still had only USB2 ports on old BIOS system.

Local Microcenter computer store was only $1 more for USB3 for same size flash drive. And I found even with USB2 port, the USB3 flash drive was about 10% faster.
Store is nearby and every time I went in it, flash drives were a bit cheaper or larger for same price. I now have too many flash drives and try to avoid the store (not really). Their house brand flash drives may not be fastest, but have always worked for me.

But I had an old 60GB SSD (early Microcenter again) and used it with a SATA to USB cable. It was faster installing to that SSD than internal HDD and almost as fast as newer internal SSD.
Then on a newer system I updated a M.2 SSD to M.2 NVMe drive and put M.2 SSD into a M.2 to USB converter. It is fast.  I have lots of flash drives and now may not buy any more, as SSD is so much better as external drive.

I do not trust main working drive for more than about 3 years, even if warrantee is longer. So I may soon have another SATA SSD I can convert to external use. Then I can keep using it for years, hopefully.

---

