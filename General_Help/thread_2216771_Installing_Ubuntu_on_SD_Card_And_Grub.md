---
title: "Installing Ubuntu on SD Card? And Grub?"
date: 2014-04-13
forum: General Help
---

### Post by Lukasz Tarkowski on 2014-04-13
Hey everyone My Asus 1225B can see SD cards and I can boot from them.  Now how do I install Ubuntu on A SD Card and Grub on it?  How do I reinstall grub on a SD Card if it gets messed up

---

### Post by coldcritter64 on 2014-04-13
If you mean running a full installation as if the SD card were your hard drive. That  would be the same as a normal full installation but only the installer is told to install to the block device for the SD card and NOT to your HDD. *_Same for the grub bootloader, during installation ensure you point the installer to the SD card device, once again  "not your HDD"_*.

Using the normal live cd/dvd installer you need the "Something else" option, to get to the partitioner. 

IMO, it is best to prepare the SD card and its partitions in gparted prior to using the installer (you can actually set up partitions on the SD card with the ubuntu installer, I prefer to do so before using the installer for ease of use when in the installer). If you pre-partition the SD card you will see the partitions for your install waiting to have a filesystem allocated for them here (in the installers partition tool).

Point (or make and point to) your partitions for root, home, swap (if you need it) here and later on in the installation process ensure the grub bootloader is pointed to the block device of the SD card eg /dev/**sdb** DO NOT point it to a partition eg /dev/**sdb1**. 

Prior to doing the installation identify your device numbering for the SD card, with the SD inserted open a terminal and use the code,
```
sudo fdisk -l
```that is a lower case L in the code. You should be able to make yourself familiar with its device numbering using this (even off the live cd, you can use this in a terminal, just hit the enter key on your keyboard for the sudo password, ie no password is set on the live cd/dvd.)

>  How do I reinstall grub on a SD Card if it gets messed up         Same as for the main installation boot in to the laptops linux install (if it has one, I am assuming it has) or even a live cd, chroot into the install on the sd card if necessary and reinstall grub to the SD card device. If you can access the forums off a live cd, even if you kill grub on the laptop it can easily be fixed from a live cd/dvd and questions/guides here.

One last piece of advice: _*Do a complete backup of the laptop drive before messing with a partition tool or installer and the SD card*_. Installing to the wrong device can be catastrophic to any existing installations (Windows or Linux).

Here is an "askubuntu" link, for manual installation, that may help you : [http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation) It covers various installation scenarios.

---

### Post by Lukasz Tarkowski on 2014-04-13
Is SD Card 16 GB Enough for Ubuntu and Updates, and some games.

---

### Post by coldcritter64 on 2014-04-13
> **Lukasz Tarkowski said:**
> Is SD Card 16 GB Enough for Ubuntu and Updates, and some games.

Yes 16GB should be more than enough. Though I don't know how it'll perform for gaming from a SD or USB, I use such installs as general purpose tool disks / portable OSes.

I generally allow about 7.5 to 10 GB for /root, /home the rest, maybe a small swap partition as well. 
With 16GB, one 8 GB for root, one 7.5GB for home, and one 512MB (0.5GB) swap partition is how I'd do a usb stick or SD card. 
I don't think swap is necessary but generally allow a small amount if I use the usb sticks on different hardware; that way I don't rely on the uuid of a fixed HDD's swap partition being used by the partitioner clashing with me moving between differing hardware setups, you carry your own swap for the SD install on the SD card that way.

I'll say again though, back up the laptop for your own good. Losing an installation with partitioners / installers is VERY easy to do, doing this sort of task. Take care.

Edit: I should also note, don't expect very long life from an install on USB or SD cards. The read/write cycles of running an OS on them can cause hardware problems over time, to avoid such I regularly back up the home partition and the root partition of such installs to an image file on my desktop HDD storage volumes; for **when** the usb stick fails. Expect similar running problems down the track using an SD card, backup your work on it regularly. Cheers.

---

### Post by Lukasz Tarkowski on 2014-04-13
Thanks for your help, I will install small games provided by Ubuntu, and skype

---

