---
title: "How to boot Ubuntu 12.10.ISO on a virtual CD drive by daemon tools?"
date: 2012-12-04
forum: General Help
---

### Post by AmirRazoR on 2012-12-04
hello, i am very new here, i downloaded the "Ubuntu 12.10" as an .ISO file and i opened it with deamon tools, and deamon tools created a virtual CD drive for it, something like "DRIVE (H: )", but now that i want to install ubuntu, i couldn't get my system to boot this, what should i do so system would boot this and i could install it? or go to the demo ubuntu?[SIZE="2"][/SIZE]

is there any way to do it without burning into a CD or flash drive?

---

### Post by Cheesemill on 2012-12-04
You can't use Daemon Tools to install Ubuntu like this. The reason being that Daemon Tools only runs after Windows has loaded but to install Ubuntu you need to boot the ISO before Windows has loaded.

The only easy options are to burn the .iso to a DVD or install from a USB drive.

---

### Post by oldfred on 2012-12-04
There is another option but you have to be booting with grub2 either from a USB flash drive or another hard drive. 

       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

    
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

---

