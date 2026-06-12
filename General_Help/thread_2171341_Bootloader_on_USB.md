---
title: "Bootloader on USB"
date: 2013-08-30
forum: General Help
---

### Post by raed3 on 2013-08-30
For security reasons I want to istall my OS on the hard drive, but the  bootloader on a USB stick .. (with the bios setting to boot USB first) 

So that when the USB is loaded it has the grub bootloader (or other) that points to the OS installed on the hard drive,


Possibly  I could have another secondary bootloader installed on the hard drive  configured only to a certain Decoy OS (windows system or something) to  fool whoever looks at the computer without that specefic USB  stick ..

---

### Post by nerdtron on 2013-08-30
You can do it in the Manual partitioning in the "Do something else" option in the Ubuntu installer. Example:
USB1 - This is the install media with ubuntu, You boot from USB to install Ubuntu OS on the hard drive.
Hard Drive - on the manual patitioning screen you should define at least 2 partitions, one is "/" partition as ext4 and the other is a small "swap" partition.
USB2 -  on the lower part of the manual partitioning screen you'll have the option on where to install the boot loader. You should choose the USB2 here, it could be /dev/sdc. Don't forget to choose the drive it self and not a partititon (/dev/sdc1 is wrong). Also this flash drive will be formatted.

---

### Post by raed3 on 2013-08-30
Thank you ... but 2 questions ... can't this be done afterwords ?
and 

I didn't really get the part 

> . Don't forget to choose the drive it self and not a partititon (/dev/sdc1 is wrong).

---

### Post by sudodus on 2013-08-30
Write the bootloader to the head of the drive, which is written as ***/dev/sdc ***for device c, while /dev/sdc1 is wrong because it points to the first partition on that drive, which is off-set 'further down' from the head of the drive.

If there is an MSDOS partition table, the MBR (master boot record) and the partition table are situated in the first 512 bytes. Newer systems also need more space at the head of the drive, so normally the first partition starts after one megabyte. This is done automatically, when you make partitions with ***gparted***.

---

### Post by oldfred on 2013-08-30
If after your install you can install grub to another device, but it will not replace the boot loader in the MBR of the hard drive unless you install something else. Use sdb or whatever is the USB flash drive shown by fdisk.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

Grub also remembers where to reinstall. I am not sure above changes this setting. You can check before and after above commands and see where it will reinstall. You can either make it alway reinstall to flash drive, but if not plugged in, will get errors on a grub update. Or you can just uncheck everything and it will not reinstall. But on a major update may get out of sync. Best then to have live installer to repair.
      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by VMC on 2013-08-30
I just did this very thing for testing a grub script. I have an old 256mb usb stick, that I used.

Using my Ubuntu, I installed usb, then issued: 
```
sudo grub-install --recheck --root-directory=/media/OTI /dev/sdd
```

It put grub on the usb partition, and built "/boot/grub" folders on that usb.
Then I just copied my grub.cfg off my Ubuntu and placed it on the usb device.
When I booted I selected the usb, grub menu came up exactly as the Ubuntu grub.cfg does, and I booted the Ubuntu off of the usb grub.
See below for bootinfoscript results:
```
============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.
 => **Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of **
**    the same hard drive for core.img. core.img is at this location and looks **
**    for (,msdos1)/boot/grub on this drive**.
```

---

### Post by oldfred on 2013-08-30
The advantage of VMC's method is that a full grub is installed to the flash drive not just the MBR boot loader. With just the MBR you have to have working hard drive with the rest of grub. If you have issues you may be able to edit grub that you boot from the flash drive with VMC's full install of grub.

---

