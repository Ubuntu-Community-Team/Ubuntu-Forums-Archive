---
title: "Unetbootin for OS installation"
date: 2022-08-14
forum: General Help
---

### Post by sofasurfer on 2022-08-14
Unless I am misunderstanding, Unetbootin can be used to install a second operating system without using a DVD or USB.
I am currently running Xubuntu. I installed Unetbootin, I downloaded debian.iso and did what I read that I should do. I opened Unetbootin, I chose the iso option, I surfed to my debian.iso download and then clicked "OK". I updated Grub and then restarted my computer. When the menu came up there was no entry for debian or unetbootin.
Where did I go wrong?

---

### Post by sofasurfer on 2022-08-14
I did not have my partition formatted. Now it is formatted and I have a debian icon on my desktop. When I click it nothing happens. I opened Gparted and the partition IS being used but what is in it is only 530mb in size. From what I have read this is probably a minimal install (maybe thats the wrong term). If I could get it to launch it may have a option for try/install like on a live dvd. 
Any ideas?

---

### Post by yancek on 2022-08-14
You should see a unetbootin option in the Grub menu from Xibuntu.  You are doing what is referred to a a frugal install which is described in some detail on the page below at the link below.  There is an option in Unetbootin to use the Hard Disk Install mode and if you select this option, you should see a unetbootin entry in the Grub menu.  This should boot the same way booting from the USB and will be the live environment.  You will need to have your drive partitioned with a Linux partition prior to running the installer.

If you've read the link below and used this method, I'd just try it again and make notes of each step to compare to the instructions later.  Good Luck.

[https://sourceforge.net/p/unetbootin/wiki/installmodes/](https://sourceforge.net/p/unetbootin/wiki/installmodes/)

---

### Post by sudodus on 2022-08-14
You are right, it is possible to use Unetbootin to install a second operating system without using a DVD or USB. I have read several reports about it, but I have never done it myself, I prefer using a USB drive.

It is much easier to install an operating system using a USB drive or some other 'extra' drive, that is temporarily dedicated for the purpose. It can also be connected via eSATA or internally. You can even use a memory card, if the computer can boot from it.

---

### Post by C.S.Cameron on 2022-08-14
I have not been able to get UNetbootin **Frugal** install working since Ubuntu 20.04 came out.

---

### Post by yancek on 2022-08-14
Since you hae Xubuntu install which used Grub2, you can boot the iso file from the Xubuntu / (filesystem partition.  A sample boot entry below.  You will need to change (hd0,gpt3) to whatever partition Xubuntu is on.  On the loopback loop line you will need the exact name of the Debian iso as well as the correc patht  If it is in your user Download directory, change it to /home/user/Downloads/debian-live-11.4.0-amd64-cinnamon.iso.  On the linux (loop) line you will need the UUID of the partition on whcih you have the iso and again the full path to it.  Put this entry in the /boot/grub/grub.cfg file of Xubimti and do NOT update Grub.

> menuentry "Debian 11.4" {
        loopback loop (hd0,gpt3)/debian-live-11.4.0-amd64-cinnamon.iso
        linux (loop)/live/vmlinuz-5.10.0-16-amd64 isofrom=/dev/disk/by-uuid/45f8d0f7-05c4-4012-89c1-e088f0852071/debian-live-11.4.0-amd64-cinnamon.iso boot=live components quiet splash --
        initrd (loop)/live/initrd.img-5.10.0-16-amd64
}  

---

