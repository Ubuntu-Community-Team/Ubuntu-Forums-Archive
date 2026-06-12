---
title: "repair usb"
date: 2014-03-02
forum: General Help
---

### Post by NyteRukh on 2014-03-02
hi..i have switched completely to Ubuntu linux currently running Ubuntu 13.10 64 bit on a lenova g530 laptop there have been some issues where i couldnt boot into ubuntu...and had to reinstall everything.what im wondering is if its possible to create a repair usb so i can repair whats wrong instead of downloading everything and starting all over

---

### Post by oldfred on 2014-03-02
Your live installer is a repair flash drive.

I have several flash drives. I used to always burn several LiveCD for repairs like gparted, parted magic, current Ubuntu version, Knoppix, Boot-Repair, Supergrub. And since I was installing a test version or new version every 6 months when a new one came out and the versions of the repair tools also updated I was burning a lot of CDs.

So I found you can directly boot an ISO with grub. I now boot ISO from one hard drive to install to another hard drive but also have several flash drives with all the repair ISO and a larger flash drive with a full install of Ubuntu as a another way to boot in an emergency as laptop only has one drive.

       This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)


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


There are a variety of tools/scripts to automate the process. I started before they were available, and prefer to understand grub2 and how to create boot flash drive. But scripts simplify process. Not all use grub2.


 These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
[https://sourceforge.net/projects/multibootusb/files/](https://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
[http://ubuntuforums.org/showthread.php?t=2175738](http://ubuntuforums.org/showthread.php?t=2175738)
Uses grub4dos to boot many ISO and other bootable files
[http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1](http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by grahammechanical on 2014-03-02
In Linux, as in other operating systems, re-installing is often the easiest and quickest way to fix things. We also have the Ubuntu live session which can give us access to the power of Linux terminal commands and with them we can sometimes repair or fix what is wrong.

By the way, we also get access to Linux terminal commands in the Ubuntu Recovery Mode menu. The options are

resume - that loads to a desktop without using a proprietary video driver.
clean - try to make free space.
dpkg - repair broken packages
fsck - check all file systems
grub - update grub boot loader. It does not re-install Grub.
network - enable networking. It gets us internet access.
root - drop to root shell prompt. It allows to use Linux terminal commands which we can then use to edit system configuration files and re-install Grub.
system-summary - produces a summary of our system.

So, in one sense we already have a repair disk installed on the disk. I have omitted failsafeX because it seems to be broken as far as I can tell.

What do you think a Repair Disk would have on it? No set of diagnostic utilities would be of any benefit if you did not no how to use the tools. We could do more damage and then a re-install would be the better option.

I must not fail to mention Linux Secure Remix. It is based upon Ubuntu. It has a tool for repairing the boot menu, an OS uninstaller tool and clean-ubiquity which can make a backup of the MBR.

[http://sourceforge.net/projects/linux-secure/](http://sourceforge.net/projects/linux-secure/)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

[https://launchpad.net/clean-ubiquity](https://launchpad.net/clean-ubiquity)

None of these utilities will be of any use if we do not know what they do and cannot understand the information being provided by them. This is where I often fall down.

Regards.

---

