---
title: "ubuntu 14.04"
date: 2015-11-11
forum: General Help
---

### Post by okkie2 on 2015-11-11
i want to install windows xp pro next to ubuntu. how do i create a partition for it

---

### Post by Bucky Ball on 2015-11-11
Install Gparted, launch it, shrink partitions to make free space if you have to. WinXP install will let you make a partition for xp prior to the install. Let Win do that and create an NTFS partition with it and point the xp install to it. You can create an NTFS partition with Gparted but might be better to create the partition from the free space during xp install.

(PS: To improve you chances of support in future I suggest you use descriptive thread titles. This one is not related to and gives no information about your support request. :))

---

### Post by howefield on 2015-11-11
> **Bucky Ball said:**
> Install Gparted, launch it, shrink partitions to make free space if you have to...

Best to use gparted from a Live USB stick or DVD for this.

Sounds probably that you only have ubuntu on the disk at the moment ? Gparted will work only with unmounted partitions.

---

### Post by Bucky Ball on 2015-11-11
> **howefield said:**
> Best to use gparted from a Live USB stick or DVD for this.

Sounds probably that you only have ubuntu on the disk at the moment ? Gparted will work only with unmounted partitions.

Doh. Excellent point! What howefield said. Just got back from dinner and must have left my mind at the eatery with the Nepalese spices! :)

---

### Post by ajgreeny on 2015-11-11
Unless things have changed since I last installed Windows, you will also find that XP has taken over the bootloader and Ubuntu will not be available when you next boot.  You will need to reinstall grub to the MBR of the hard disk, which you can do either using **Boot-Repair** in my signature below, or direct from the live DVD/USB.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If your machine is using UEFI you will not be able to install XP, as far as I'm aware, as I don't think it is a UEFI enabled operating system.  You may, however, be able to change the system to BIOS/legacy boot without reinstalling Ubuntu, which I believe can be done using Boot-Repair, though I have never done this.

---

### Post by okkie2 on 2015-11-11
you are all so kind. My main reason for installing windows is to use it to format a hard disk for me first and install windows on it afterwards to avoid the problems I had in the past.
Can ubuntu 14.04 assist me to format a hard disk ?

---

### Post by grahammechanical on 2015-11-11
Ubuntu has utilities that can format hard drives. The Disks utility in installed by default and will do that. And Gparted will also do it but it is not installed by default. That is one reason why we run Gparted from a live session.

I should have thought that a Windows install CD would have utilities to format hard disks and create partitions.

Regards.

---

### Post by Bucky Ball on 2015-11-11
Yep. The Win install should take care of all that without having to partition the drive beforehand, as far as I remember. It gives you the option to create a partition to install to if it finds none.

As mentioned, Gparted can create NTFS partitions. I'd leave it to Win, though.

---

### Post by okkie2 on 2015-11-12
Thanks a lot once again everybody. This will certainly see me through.

---

