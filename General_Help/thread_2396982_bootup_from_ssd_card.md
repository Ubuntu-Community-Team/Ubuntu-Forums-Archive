---
title: "bootup from ssd card"
date: 2018-07-23
forum: General Help
---

### Post by ramanterola on 2018-07-23
Greetings!

I am working with a low end dell 3452 laptop : small emmc harddrive, little memory, celeron chip.   Anyway,  Is there a way to boot up from the sd card reader?   Or maybe boot up to grub and redirect the OS load.

I have a 128GB sdcard and if at all possible, I would like to use it, maybe have this laptop set up as a dual boot.

Thx

RM

---

### Post by mIk3_08 on 2018-07-24
[Click here]("http://ubuntuforums.org/showthread.php?t=2130640") for some information about old Hardware.
then try [Xubuntu]("http://xubuntu.org/")
and [lubuntu]("http://lubuntu.net/")

---

### Post by ramanterola on 2018-07-24
Hi mlk_08  

I read the link article top to bottom and couldnt find anything related to my question.     I would ultimately run Lubuntu 18,  which has run flawlessly when booted from the USB.

My question is different:   Can I boot up from the SDcard reader?   If so, how do I do that?    or another way would be to boot up to grub on the 32gb Emmc and then redirect the full OS load from the SDcard reader.

Thx

R
[COLOR=#000000]mIk3_08[/COLOR]

---

### Post by rrnbtter on 2018-07-24
Greetings,
The SD card requires kernel support and you don't get that support until boot, therefore you can't boot from SD. Since USB is supported from bios you can boot from USB.  I don't see why you can't put your boot sector on USB and OS on SD. Might be fun to try,

---

### Post by ramanterola on 2018-07-25
Hi rrnbtter,

That is exactly what I am trying to do.   I have a 32 GB Emmc drive that I can use to boot up (boot sector), and then load the OS from the SDcard.    Do you know how to do this?

Thx

R

---

### Post by coffeecat on 2018-07-25
Support, not chat. *Thread moved to **General Help**.*

---

### Post by C.S.Cameron on 2018-07-25
I have a 128GB SSD.
I only keep my Ubuntu OS and other program installs on the drive.
I keep home on a spinning drive as well as all my other storage.
/etc/fstab is where to specify home directory location. 
see also [https://www.maketecheasier.com/move-home-folder-ubuntu/](https://www.maketecheasier.com/move-home-folder-ubuntu/)

---

### Post by oldfred on 2018-07-25
UEFI or BIOS.

If UEFI, you just need emmc internal card gpt partitioned with an ESP - efi system partition which is FAT32 with boot flag.
A typical UEFI Ubuntu install to any external device defaults (usually incorrectly) to install grub2's boot files into the first internal drive's ESP. In your case that may be what you want.

If you want to use internal emmc card:
[https://askubuntu.com/questions/879986/emmc-boot-installation-compatibility/883179](https://askubuntu.com/questions/879986/emmc-boot-installation-compatibility/883179)

---

### Post by Geoffrey_Arndt on 2018-07-27
I would suggest you consider a "full install" to an external SSD (not an SD card or usb flash-stick).   And not a Live or Live/Persistent setup.    In my experience, this is the only "Quality" way to run any mainstream Linux distro (exceptions being distros expressly designed for Live Media - - such as Parted-Magic, Knoppix, SystemRescue CD, Kali, ParrotOS and similar).

You utilize a USB flash-stick with the installer image to target the install to the attached portable usbv3 SSD (preferably via a faster v3 usb port).   The result is a very fast system that is now_ fully update-able_.  (note, the other types are not - including persistent setup).

This link shows what I've used for several years - - am using this now running ElementaryOS Loki on a 480 GiB usbv3 ssd.   

[https://www.youtube.com/watch?time_continue=2&v=4qtr9QaYJ7U](https://www.youtube.com/watch?time_continue=2&v=4qtr9QaYJ7U)

**Note**:  you can get one of these devices on Amazon (120Gib) for about $69 or $79.    Well worth the few extra $ if you can afford it.

---

### Post by marciomj on 2018-07-29
[**[COLOR=#000000]ramanterola[/COLOR]**]("https://ubuntuforums.org/member.php?u=2098493"), if You don't run much software on Ubuntu, I believe You can install it to Your emmc card, and point Your home partition to SD Card.

I don't use any special software in my Ubuntu Machines. I normally leave the OS partition with 30GB, and the OS + apps combo didn't take more than 20 GB.

For special software, I normally use virtual machines, and I run these from my Home partition, or from an external HDD.

---

### Post by HermanAB on 2018-07-30
Yes, you can boot off a SD card.  I have done so in the past.  However, you may have to compile the kernel yourself and load the SD card device driver module into the kernel, so that the machine can get going.

As a modern day example, Raspberry Pi computers run off a SD card.

---

### Post by ramanterola on 2018-08-01
Thank you for the input, but I am not sure if what I am trying to do is possible.

This little toy of a laptop fits my needs; its light, battery lasts a long time, inexpensive so I dont mind putting in my backpack and getting beat, etc.  I want to keep using it: Windows 10 as we know is a resource hog, and I am moving quickly to open source across the board.  Having said that,  I need to keep windows available (ugh!!!).   

The Dell Bios does not recognize the ssd card slot as a bootup device.  I am thinking that if I can put GRUB on the 32gb Emmc and from there, I can load the SSD card drivers and use the SSD as my primary "harddrive".    I have been able to put windows 10 & Lubuntu on the Emmc card independently, so that is not a problem.   

If Dell would have spent another $5 and upgraded the 32gb to a 64 gb, I would have enough space to partition the Emmc and be able to install both OS in the Emmc, and any apps on the SD card, but 32gb is barely enough to install windows.

So to ask my question again:    turn computer on, BIOS loads, GRUB or similar allows for selection of OS including OS on SSD.     Any ideas?

Thank you again for your time and expertise.

R

---

### Post by ramanterola on 2018-08-10
Anyone?

Bueller?

---

### Post by oldfred on 2018-08-10
You never said if UEFI or BIOS?
Post this:
sudo parted -l

All my UEFI installs only boot from one ESP on the drive seen as sda. In your case that will be the first MMC card?

---

### Post by ramanterola on 2018-08-14
Oldfred:   UEFI

I cannot do provide you with the sudo printout because right now I am running Windows 10 because of needing certain software, and quickly running out of disk space.

This machine is so close....I would configure it in anyway needed (using GRUB or a partition tool etc) that would allow me to push the OS to the sdcard.

Thank you for your help.

R

---

### Post by oldfred on 2018-08-14
Default install will put UEFI boot loader in the first drive.
When you say you are booting from SD card is that the internal EMMC or an add in.

I would just partition SD card to gpt and / (root) partition. Then boot installer in UEFI mode and install to SD card. Grub boot will be on ESP on internal EMMC card. that may be all  you need.

Even though one of my systems has an SD card reader, I normally use a USB/SD adpater and then SD card is seen as USB device. Have not tried installing to that, though.

---

### Post by ramanterola on 2018-08-14
Oldfred,  

The computer has a 32 gb emmc drive, 3 usb ports & a sd card slot.    I keep on referring to the sdcard because I currently have a 100gb sdcard there and nothing sticks out of the computer.   I need to maintain Windows 10 for certain software, but I like running Ubuntu & Lubuntu.    Since I have 100gb available,   My idea is to boot up to the 32gb emmc drive, and have a utility (i.e GRUB) that allows me to choose the operating system that I want to use which would be installed in separate partitions on the sd card.

32 gb is just small enough that I cannot install Windows 10 & another OS, hence the usage of the sdcard.    I also have a 100gb usb drive, but it sticks out of the computer so I am afraid that a small hit will damage it.

If you have a better way  - - I am open to suggestions.

Thx

R

---

### Post by oldfred on 2018-08-14
Until you try it we will not know.
But I think since grub will install to internal drive's ESP, it will still boot and work.

Once partitioned it takes me 10 minutes to install to an SSD, but 45 minutes for a full install to a flash drive. Not sure how fast writes are to your SD card.

---

### Post by ramanterola on 2018-08-17
Oldfred,

I simply do not know how to try it, it is the help that I am seeking.

How can I install GRUB or another lowlevel boot to the primary internal drive (32gb emmc), this low level will have to enable the SDcard slot, to where I can then use it to load the operating system of my choice.

Is this even possible?
Can you walk me thru such type of installation?

Thx

R

---

### Post by oldfred on 2018-08-17
Did you try an install?
Standard install wants to install grub to first drive. 
But you have to know if internal is UEFI or BIOS, so you install Ubuntu in same boot mode. 

You can directly install grub to just about any device, but it installs not just a boot loader, but other files also. And then you normally have to maintain grub.cfg (the menu) with what ever boot stanza you need to boot your systems. If grub is installed as part of an install or reinstalled from within an install with chroot or Boot-Repair then grub has its own tools like os-prober that add other system's boot to grub menu.

If you can boot your install, if drive is sdb:
       sudo grub-install /dev/sdb 
Your MMC may be like this:
sudo grub-install /dev/mmcblkXX  #where XX is your device number
sudo parted -l

---

### Post by ramanterola on 2018-08-22
Oldfred,

I have to be honest...I am googling how to install GRUB.   The reality is that I do not know how to install grub without installing an OS.

R

---

### Post by oldfred on 2018-08-22
UEFI or BIOS?
You need Ubuntu or live Ubuntu, but not Windows to install grub directly.

I used to install grub to a flash drive to directly boot ISO with loopmount. Now most of my flash drives are larger and I just do a full install and still boot the ISO.

Some examples of my BIOS based installs to flash drive with various labels.
       Label partition - if label is grub2 & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
Newer versions automount with $USER name also, this one labeled MC4GB
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
Install grub2 2.00 boot loader to gpt partitioned flash drive from Raring (it used media/fred as mount)
mount and label is PreciseInstaller and flash is sde. Note space before /dev/sde
sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde 
    
UEFI installs to flash drives, need --removable:
       sudo grub-install --target=x86_64-efi --boot-directory=/mnt/sdb1/EFI/BOOT --efi-directory=/mnt/sdb1 --removable
mounted the USB EFI partition at /media/test and I installed grub with
sudo grub-install --target=x86_64-efi --efi-directory=/media/test --bootloader-id=grub --removable --recheck --debug 

But if you directly install grub to a device, you must then manually create your own grub.cfg.
I have always created my own, but I have this in my notes.
      
 This will create a grub.cfg or you can just copy your own grub.cfg into /boot/grub
sudo grub-mkconfig -o /media/fred/PreciseInstaller/boot/grub/grub.cfg

---

### Post by ramanterola on 2018-08-24
Oldfred,

My BIOS is set to FASTBOOT, UEFI, Disabled secure boot, Disabled load legacy options.

I got to a GRUB screen.   It has a text like this:

=================================
GNU GRUB Version 2.0[CENTER]
[/CENTER]
[LEFT][MinimalBASH-like line editing is supported. For the first word , TAB    lists possible command completions. Anywhere else TAB lists possible   device/file completions. ]
grub>[/LEFT]
=================================

When I run ls from the grub command, I get the following:  (HD0),(HD0,gpt1),(HD0,gpt2),(HD0,gpt3).  If I do an ls in any of these devices, I receive the message "Unknown filesystem" for all the devices.   

At this point, I am stock.

Thank you again for your time and expertise.

R

---

### Post by oldfred on 2018-08-24
Can you boot from flash drive?
If so run this:
       Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.

I have used memory cards in a USB reader. I have not tried booting from that, but since it looks like flash drive, I would expect that to work. USB readers for flash drives are inexpensive.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ramanterola on 2018-08-27
OldFred,

The URL for the boot repair results is: [http://paste.ubuntu.com/p/yRpkcPVH6d/](http://paste.ubuntu.com/p/yRpkcPVH6d/)

/dev/mmcblk0:  Is the 32Gb Emmc harddisk built into the machine. This is where I currently have Windows 10, which I would like to keep
/dev/mmcblk1:  Is the SSD card where I would like to point GRUB to load Lubuntu
/dev/sda:      Is the USB drive that I booted the machine from. I dont want to boot from this unless it is for installs.

What is the next step?

R

---

### Post by oldfred on 2018-08-27
Script does not parse MMC cards well.

But it looks like somehow you installed grub in UEFI boot mode, but have nothing for it to boot. You normally install Ubuntu and that installs grub to boot your Ubuntu install.

And it looks like you converted one of Microsofts required partitions to ext4, mmcblk0p2, that normally would be unformatted and have the Windows reserved flag.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

It also looks like you used your SSD as installer. Most tools you use to create installers erase entire drive. And many make it somewhat difficult to convert drive back as they use dd to create a hybrid DVD/flash drive configuration, that does not have partitions and just has data in area normally used by partitions. Then partition tools have difficulty creating partitions. Probably worthwhile to buy a small flash drive to use as installer and keep as repair flash drive. Also get another some what larger one, whether you install Ubuntu or not, to use as a Windows repair/recovery flash drive. You create that from your Windows.

You may need this to be able to reuse SSD. If it is just FAT32, then it probably is ok, but you only need 2 to 3GB for installer and rest of drive can be anything. Windows used to only see first partition on external drives, not sure if they fixed that, since many now have larger external devices.

 [https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive) 

You should just do a standard UEFI install to you second MMC card. I still would format in advance and include an ESP on it, but installed will normally install grub to first drive in folder next to Windows in ESP and boot second device.

      
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
Ubuntu now uses swap file, so swap partition not required.

 [http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 

Then install Ubuntu using that partition. You have to use Something Else and choose (change button) the partition for / (root). 

[https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration](https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration)
[https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

---

### Post by ramanterola on 2018-08-28
Good Morning OldFred,

I want to start with gratitude for the amount of patience and attention that you are paying to this post.

I read your entry, and I am hoping that if I have GRUB installed - Can I add a menu to it that I can direct it to either read the 32gb with windows 10 or the 128 gb with Lubuntu?

I am attaching a screenshot of Gparted for my mmcblk0 drive (which is the 32gb harddrive built into the machine - currently running windows 10 ).  My 
idea all along has been that if I the computer boots to a small partition in this drive, and then I use GRUB to load the OS from other devices.  Based on my very shallow knowledge this device would be /dev/mmcblk0p1. If this is not a correct assumption, please let me know.

[IMG]http://i68.tinypic.com/153688h.jpg[/IMG]

---

### Post by oldfred on 2018-08-28
You have an exclamation ! point next to mmcblk0p2. If you click or right click does gparted explain error?
The Microsoft reserved must be unformatted, you converted to ext4. Best to convert back.
When you installed grub did it install some files into that partition?
Or is it just inside the ESP.

The grub in the ESP - efi system partition has all you need. And it with normal installs has a grub.cfg with just a configfile (chainload) to the full grub.cfg in your install whether on same drive or not.
I do not know details but have seen some discuss having all the boot files in the ESP and not even using grub. 
I believe I once used the ESP to boot my ISO on a flash drive. I just edited a grub.cfg to loopmount them. But now I normally boot ISO on my HDD or SSD.

Do you have /EFI/ubuntu folder in your ESP? And does it have a /EFI/ubuntu/grub.cfg?

I still think you are making this a lot more difficult than required.
You can just install Ubuntu to mmcblk1 and it will automatically want to boot from mmcblk0. Ubuntu's version of grub always installs & boots from first drive and does not give user a choice. I prefer a choice as sometimes I want grub on same device as install.

---

### Post by ramanterola on 2018-08-28
OldFred,

Right now Im running W10 (which stinks, and I am quickly running out of space, but I need it.), so I do not know of a way to see the contents of the EFI system partition.  But, I am understanding your post right, I should be able to install Lubuntu to [COLOR=#000000] mmcblk1 and the installer will configure the booting menu to allow me to select the OS.   Is my understanding correct?    At that point I will have completed my need.

Please let me know if I am understanding you correctly.

I sincerely appreciate your time and your sharing of expertise.

Thx

R[/COLOR]

---

### Post by oldfred on 2018-08-28
Windows does not not normally show the ESP. I believe you can manually mount it and then it is visible.

From Ubuntu's live installer you can mount it and see what is in the folders. 
It is /EFI/ubuntu, /EFI/Microsoft & /EFI/Boot. But live instaler will probably mount at /media/$USER which with live install may be ubuntu. Have not paid attention with live installer.
But when mounted with an actual install it is mounted at /boot/efi, so full path in an install is /boot/efi/EFI/ubuntu.

```
fred@bionic-z97:~$ ll /boot/efi/EFI/ubuntu
total 2440
drwxr-xr-x 2 root root    4096 Aug 24 12:32 ./
drwxr-xr-x 6 root root    4096 Aug 24 12:32 ../
-rwxr-xr-x 1 root root     108 Aug 25 06:09 BOOTX64.CSV*
-rwxr-xr-x 1 root root     126 Aug 25 06:09 grub.cfg*
-rwxr-xr-x 1 root root     126 Sep 17  2015 grub.cfg~*
-rwxr-xr-x 1 root root  122880 Aug 25 13:46 grubx64.efi*
-rwxr-xr-x 1 root root 1153336 Aug 25 06:09 mmx64.efi*
-rwxr-xr-x 1 root root 1196736 Aug 25 06:09 shimx64.efi*

```

This is a standard install's grub.cfg in the ESP. Which just then loads the full grub.cfg in an install.
```
fred@bionic-z97:~$ cat /boot/efi/EFI/ubuntu/grub.cfg
search.fs_uuid 8c92557f-cc60-438b-b1ea-ffea0adf0a1a root hd0,gpt7 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

---

### Post by ramanterola on 2018-09-30
Oldfred,

I had to give up on this endeavor. In the end, I couldnt make it work.  I bought a new computer with a larger harddrive, and I will have dual boot.   Or run a virtualbox for the portions of windows that I need.

Thank you for all the attention and assistance.
R
R

---

### Post by oldfred on 2018-09-30
Well now you can complete experiment. :)

You can from new computer do a full install to SD card and then see if that boots on old system?
Since UEFI, bit more complicated as you probably have to boot with /EFI/Boot/Bootx64.efi from UEFI on old computer. So have to create that with new computer. Or maybe first boot using USB port & reconfigure to be SD card only?

If interested, we can provide more details.

---

