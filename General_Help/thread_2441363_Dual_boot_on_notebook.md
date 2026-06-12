---
title: "Dual boot on notebook"
date: 2020-04-22
forum: General Help
---

### Post by ELMIT on 2020-04-22
I got an older Sony Vaio notebook, but it is still fine to work with.

I postponed the change of the hard disk close to the arrival day of Ubuntu 20.04

I ask here only for safety ;-)

My hard disk is too small and I will replace the hard disk of 960 GB with a 2 TB SSD. There I have to install Windows 8.1 first. I was told the serial number is in the BIOS hidden, so I want to install it first. I downloaded 8.1 DVD from Microsoft.
After installation of 8.1 including the driver program from Sony, I want to upgrade to Windows 10. The free upgrade is not anymore officially available, but a month ago I could still do it. I hope it works still tomorrow ;-)

Assuming it worked I will shrink the Windows partition from 2TB to 350 GB. I hardly use Windows, but one program is only in Windows available, ... (currently I use that in VirtualBox+Windows, but that leaves me too less RAM)
The free space I will use for Ubuntu 20.04 according to [https://itsfoss.com/install-ubuntu-dual-boot-mode-windows/](https://itsfoss.com/install-ubuntu-dual-boot-mode-windows/)

Installation type: Something else
Create new partitions for Ubuntu:
The guide suggests to create 3 partitions: /, swap and /home
Some other guides don't suggest any but /
I got 16 GB RAM on the notebook and since I use a SSD, should I use a swap partition? If so, what size is useful. Recently I saw suggestions of no, 3 GB, half of real RAM, same size of RAM. What is your opinion and why?

Rest of the installation is straight forward.

If there are some problems, how can I prepare for it. e.g.:
1. if Windows does not install, does not upgrade, can I just leave a space on the hard disk to install Windows later?
2. if for some reason I need to go back to my current hard disk, and I swap back the SSD for the old hard disk, what do I need to take care of?
(I have a work still on my Ubuntu 19.10 on that old hard disk, maybe I need that to continue, if I could not copy it over to the new Ubuntu 20.04)

BTW, I will use my old hard disk in a USB-3 enclosure to keep my data there, and move them over as needed.

Thanks for your thoughts and hints.

bye

Ronald

---

### Post by oldfred on 2020-04-22
Be sure to use gpt partitioning and boot both installers in UEFI boot mode to install in UEFI boot mode.
Windows only installs in UEFI boot mode to gpt partitioned drives.

Ubuntu now uses a swap file, so no swap partition is required. Some still suggest one and 4GB. Hibernation is not recommended and that would be the only time you need a large swap partition.

New users can just just / (root). But as you get more advanced, better to separate system from data. Easier for a newer user to use a separate /home as you can create that during install and it automatically adds it to fstab for auto mount on reboot, with correct permissions and ownership. 
If you then want data partition(s) you have to manually create those, create mount points, edit fstab and set ownership & permission. Not really all that difficult after you have done it a few times, but first time can be intimidating.

---

### Post by ELMIT on 2020-04-23
> **oldfred said:**
> Be sure to use gpt partitioning and boot both installers in UEFI boot mode to install in UEFI boot mode.
Windows only installs in UEFI boot mode to gpt partitioned drives.

This I don't understand.
I will use a Windows installation DVD and install on a new  SSD the system.

I read it so, that Windows disk program allows me to shrink the Windows partition. Then booting with the Ubuntu DVD and install at the free space, whereby I use customize settings so that I can create two ext4  partitions mounted to / and /home

How do I gpt partitioning ... ?

---

### Post by dragonfly41 on 2020-04-23
[COLOR=#000000]> BTW, I will use my old hard disk in a USB-3 enclosure to keep my data there, and move them over as needed.

If you have USB-3 then you have fast USB speed and you could (as just one option) install Ubuntu on this external USB drive (GPT mode not MBR to gain advantage of UEFI) with partitions
/dev/sdb1 ESP 500M fat, boot flags
/dev/sdb2 Ubuntu mounted at / .. ext4 
/dev/sdb3 swap

I would then install your Windows on its own nest in internal SSD.
Later you might think about using some of the SSD 2TB but that initial setup will get you going and keep the two OS apart.
Your data could be in ext4 partition in your internal drive (SSD).
Later you can juggle these around.
Remember that you need some backup device(s).
I would also install rEFIind in external /dev/sdb1 but that is my own personal preference rather than relying on Grub.
[/COLOR]

---

### Post by oldfred on 2020-04-23
Windows requires gpt partitioning with UEFI boot, so if you boot installer in UEFI mode it will automatically be gpt partitioned.
Ubuntu does not require (but should) gpt partitioning for UEFI install.

For general UEFI install instructions see link below in my signature. 
Also more info on what gpt is and its advantages.

Other posts with Sony have had dual boot issues. 
Make sure you have newest UEFI from Sony and update firmware for SSD before Ubuntu install.

Dragonfly1's suggestion of rEFInd may be required or easiest solution.

Have not seen many Sony post's recently. I try to save common issues to my own text file.
The renaming is not not normally now required as grub installs a copy of shimx64.efi into /EFI/Boot and names it bootx64.efi for hard drive or fallback boot. Boot-Repair also does the copy & rename.

Sony VAIO E-series  19.10  Used rEFInd, could not otherwise change boot order
[https://ubuntuforums.org/showthread.php?t=2431243](https://ubuntuforums.org/showthread.php?t=2431243)
 HOWTO: Sony Vaio Pro 13 DualBoot (Win 8 + Ubuntu Trusty 14.04) SecureBoot Wifi LVM
[http://ubuntuforums.org/showthread.php?t=2227580](http://ubuntuforums.org/showthread.php?t=2227580)
 Sony Vaio Pro 13 - To get into  UEFI press this "Assist" button BEFORE starting
[http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio](http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio)
[http://askubuntu.com/questions/644901/booting-a-sony-vaio-computer-running-windows-8-1-in-ubuntu-from-a-usb-drive](http://askubuntu.com/questions/644901/booting-a-sony-vaio-computer-running-windows-8-1-in-ubuntu-from-a-usb-drive)
Issues on rename
[https://bugs.launchpad.net/boot-repair/+bug/1315490](https://bugs.launchpad.net/boot-repair/+bug/1315490)
UEFI With encryption but you do not have to and with efi file boot rename
[http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/](http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/)
One Sony user, dual booting, and boot hard drive UEFI entry, not ubuntu
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)

---

