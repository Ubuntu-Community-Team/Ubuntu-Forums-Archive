---
title: "creating a bootable disk.."
date: 2013-02-06
forum: General Help
---

### Post by boyo1991 on 2013-02-06
so ive been trying this with a vast array of linux OS's, including android... i currently have ubuntu 12.10, and love it, will never go back to windows bloatware again..

but ive been having some problems, i service computers in the area, and i would like to be able to install ubuntu or really any linux os (ubuntu prefferable) for my customers. problem is, anytime i try and create a boot disk (dvd/cd/usb) it doesnt extract correctly to the drive..

on usb, after trying to boot from usb that is, it tells me that there was no operating system found...

furthermore, on cd/dvd, all that happens is that the disk keeps spinning and spinning.


the way i fix most OS problems for my customers is to reinstall the OS, its the easiest, most efficient way, and i do it on the cheap, so they dont complain.. but when i cant get my boot disks to work, theres a problem...

currently im planning on just buying a set of disks, but what about all the other .iso's id like? for example, the android x86 project that id like to get bootable?


i love linux, i may not understand it, but it allocates memory so well, and is open source and has a huge community because of it. so does anyone have any suggestions? id absolutely hate to keep doing windows xp installs (currently the only ones i am able to do due to this :/ )

---

### Post by arpanaut on 2013-02-06
This should fix you up:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Here's another option:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by C.S.Cameron on 2013-02-06
Check your ISO's MD5SUM.
Use Startup Disk Creator to make Ubuntu Live USB's.

---

### Post by oldfred on 2013-02-06
Separately to issue of creating one DVD or Flash.

You may want multiple repair ISO on one flash drive. I use grub2 and boot the ISO directly with grub2's loopmount feature. Then it is easier to update ISO as versions are always updating. Just copy ISO and edit grub menu.

I did it before several created scripts to automate the procedure. Some use different boot loaders but idea is the same.

       These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

    
       MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by oldfred on 2013-02-06
Separately to issue of creating one DVD or Flash.

You may want multiple repair ISO on one flash drive. I use grub2 and boot the ISO directly with grub2's loopmount feature. Then it is easier to update ISO as versions are always updating. Just copy ISO and edit grub menu.

I did it before several created scripts to automate the procedure. Some use different boot loaders but idea is the same.

       These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

    
       MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
    
       Install grub2 2.00 boot loader to gpt partitioned flash drive from Raring (it used media/fred as mount)
mount
sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde
sudo grub-mkconfig -o /media/fred/PreciseInstaller/boot/grub/grub.cfg
sudo chmod 777 -R /media/fred/PreciseInstaller/boot

    Then I created a /grub/iso folder and copied several ISO files for Precise and repair ISO like parted magic, gparted, and others.

---

### Post by FahadMKS on 2013-02-06
I'd recommend to use the Startup disk creator rather than the brasero so as to burn an startup disk. Check with that and if you have the issue with the cd please do check with the cd writer too as most of the burning issues can be due to some dust in the cd writer.

---

### Post by boyo1991 on 2013-02-07
well, ive tried several different methods that seemed to work for other people that didnt work for me... one of the main reasons i want a boot disk is a safe and easy way to reinstall every time i need to, and because i HATE sharing partitions with windows, but due to wubi.exe, its pretty much my only option... :/

plus, since it would help the linux community, i plan on just buying a boot disk..

thanks anywho guys! great ideas here!

---

