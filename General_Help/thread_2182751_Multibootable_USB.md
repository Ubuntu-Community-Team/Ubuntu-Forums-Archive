---
title: "Multibootable USB"
date: 2013-10-22
forum: General Help
---

### Post by AAEIV on 2013-10-22
[COLOR=#000000][FONT=Arial]I want to create a multibootable usb, that will contain some ubuntu distros(or linux in general), some windows ones as well as some non-OS iso(such as Hiren's boot DVD, Parted Magic bootble CD etc).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]As far as multi-bootable-linux distros, I know Yumi.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I thought of partitioning the usb drive and make multibootable, by making it multipartinioned and having each distro in one partition. Can that be achieved?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I also don't know how to make the Hiren's and Parted Magic's .iso's bootable in a USB.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Ideally there would be a bootloader that would help to choose wich "partition" to run from.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Can all or part these be achieved?[/FONT][/COLOR]

---

### Post by oldfred on 2013-10-22
I created my own multiple boot USB flash drive before many of the scripts became available. I installed grub2 to my flash drive and used loop mount to mount the ISO. Only ISO that are configured for that work, but I have Ubuntu desktops, gparted, parted magic and a few others. I never could bet alternative or server versions to work.
Windows will not boot from ISO, but I did just install a Windows repair from CD to flash drive, overinstalled grub and then used grub to boot both Windows repair or other Ubuntu ISO from same flash drive. Only thing to be careful of is Windows has a Boot folder and grub creates a boot folder. In Windows case does not matter, but Linux may create different folders. You have to make sure there is only one.

       These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
[https://sourceforge.net/projects/multibootusb/files/](https://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
[http://ubuntuforums.org/showthread.php?t=2175738](http://ubuntuforums.org/showthread.php?t=2175738)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[URL="http://www.pendrivelinux.com/"]http://www.pendrivelinux.com/

[/URL]
 grub2 loopmount ISO Flash drive -----------------------------------------------------------------------------
Multiple-Boot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
Examples:
Label partition - if label is grub2 & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
Newer versions automount with $USER name also, this one labeled MC4GB
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
Install grub2 2.00 boot loader to gpt partitioned flash drive from Raring (it used media/fred as mount)
mount and label is PreciseInstaller and flash is sde. Note space before /dev/sde
sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde
This will create a grub.cfg or you can just copy your own grub.cfg into /boot/grub
sudo grub-mkconfig -o /media/fred/PreciseInstaller/boot/grub/grub.cfg
Only if Linux formatted, easier with wide open permissions. 777 otherwise not normally suggested.
sudo chmod 777 -R /media/fred/PreciseInstaller/boot

Hard drive is similar, but drive and partition numbers may be different with a hard drive. Lots of examples of boot stanzas in that link.
      
 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[URL="http://www.pendrivelinux.com/"]
[/URL]

---

### Post by AAEIV on 2013-10-22
Thank you very much for your answer and for your many information.
The thing is that I am not familiaar with all the scripting you described and I am not sure if I can apply your advice.

From all those, I find Yumi the most straightforward, but I don't know how easy is to include Parted Magic and windows iso's...

---

### Post by oldfred on 2013-10-22
You cannot boot a Windows ISO.

What boot loader does Yumi use.
The scripts all are like Yumi in that they create a flash drive drive, add a boot loader and copy in boot stanza to boot ISO. But different ones use different boot loaders and the boot stanza then are different. 
I only know grub2 as that is what I use.

---

### Post by jamesisin on 2013-10-22
Yumi is very easy.  I use it a lot, especially at work.  My Yumi drive has several version of Ubuntu, many bootable utilities (like CloneZilla), and has even included Windows installers.  For Yumi you have no need to create any additional partitions.  The disadvantage is the lack of (or at least the difficulty of) persistence in your Linux distributions.

Alternatively, you could just install several Linux distributions on your thumb drive *as though it were* a regular hard drive.  You can find guides for multi-booting machines.  One important piece of advice is to expect a boot problem when you have everything installed and look at boot-repair as your final step:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you are going to user your thumb drive as though it were a regular hard drive, it's probably easiest to attach it to your thumb drive to a machine which contains no other drives.  This way you won't have to interpret which drive is the one you are trying to install everything on.

---

