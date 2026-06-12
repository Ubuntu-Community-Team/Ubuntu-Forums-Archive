---
title: "How do I install a second Ubuntu and hav it at the end of my grub list?"
date: 2013-08-22
forum: General Help
---

### Post by PopsTheSailor on 2013-08-22
I want to install a second instance of Ubuntu on my laptop. I have an unallocated partition at the end of my HDD. When I install this instance it is to use as a trial system (install software, chnage configs, etc) and won't be my primary version I want to use. I have done this in the past and when I do, it pushes it to the top of my Grub menu, makes it the default boot partition and keeps my Grub config.

How do I install my second instance, put it at the end of my GRUB list and keep my regular / primary Ubuntu instance in control? 

I know I can edit my GRUB config and change the default to boot to my selected instance but that is NOT what I want to do.

---

### Post by oldfred on 2013-08-22
Boot into your main working install and reinstall grub to the MBR. But grub remembers where to reinstall on major grub updates. You may want to reset that on test install. Either uncheck all reinstall options (not sure if updates then work correctly or not, or install to its partition which we never otherwise suggest).

 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

   #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by jjaison-daniel on 2013-08-22
Just start as a normal installation with CD/DVD.
In the partition selection, make careful to choose the new partition. and in the boot menu configuration make sure it deduct the existing ubuntu and you are having both the entries.

I didn't tried this but I feel this will work.

---

### Post by grahammechanical on 2013-08-22
To keep the primary Ubuntu in control of Grub in the MBR and hence at the top of the boot menu always update the primary Ubuntu after updating the trial Ubuntu. If the update includes either a kernel update or an update to Grub itself you will be asked to reboot. You will then find that the trial ubuntu is in control. So, boot into the primary Ubuntu and run update and then the update to the kernel will force a rewrite of the Grub configuration files and the primary Ubuntu will be back in control. Or, simply run

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

From the primary Ubuntu and assuming that you only have one hard drive (sda). I do this all the time becasue I have more than one install of Ubuntu. 

A tip to make any change over more noticable is to put a background image behind the Grub menu. Use a different image for each install of Ubuntu and then when the grub background image is changed you know that the other Ubuntu install has taken over the MBR. Look for grub2-splashimages in the software centre. Install them and you will find them in /usr/share/images/grub. From there you need to copy one into /boot/grub and the next time you boot there will be a background image to the Grub menu.

There are two little things that complicate this action. (a) You need admistrator privileges to paste into /boot/grub (b) gksu is not installed by default anymore in 13.04. So,

```
sudo apt-get install gksu
```
```
sudo gksudo nautilus
```

and now you can copy that background image into /boot/grub.

Regards

---

### Post by PopsTheSailor on 2013-08-23
Thanks for the advice. I want to make sure I run the commands propertly. Here is what I have on my HDD:

Found Windows 7 (loader) on /dev/sda1 - Original operating system that came with the laptop
Found Windows 7 (loader) on /dev/sda2 - Windows recovery partition
Found Ubuntu 13.04 (13.04) on /dev/sda9 - test / development Xubuntu
Found Ubuntu 13.04 (13.04) on /dev/sdb1 - primary Ubuntu that I normally use

The version 13.04 on dev/sdb1 is my main Ubuntu. What parameters would I use for the 
sudo grub-install **/dev/sda**

command?

---

### Post by oldfred on 2013-08-23
Two drives, now which drive are you really booting from with BIOS?
I prefer to have the Windows boot loader in the MBR of the Windows drive and the Ubuntu grub2 boot loader on the Ubuntu drive. And then in BIOS set the Ubuntu drive as default boot, with Windows as second choice.

Then I would boot into sdb1 install of Ubuntu and run this:
sudo grub-install **/dev/sdb**
sudo update-grub
And set BIOS to boot from sdb.

If your install in sda9 has taken over the MBR of sda, I might either use Windows to repair its MBR with the offical Windows boot loader with fixMBR command or install from Ubuntu a boot loader that will work exactly the same as the Windows boot loader, since the old Lilo boot loader also used boot flag to know which partition to boot from.

 Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader to boot partition with boot flag (Windows).

Boot-Repair can also do this, it installs the syslinux boot loader which also works like Windows boot loader. But you have to turn off its auto repair, tick the update MBR choice and in advanced options choose which system to install to which MBR.

---

### Post by PopsTheSailor on 2013-08-28
The above didn't work so I installed Xubuntu then ran boot repair and that fixed it.

---

### Post by dragonfly41 on 2013-08-28
Perhaps a bit too late to suggest other ideas .. but I have a "secondary" instance of Ubuntu running in Virtual Box.   
The two instances of Ubuntu (desktop + headless) can communicate as separate servers.

---

