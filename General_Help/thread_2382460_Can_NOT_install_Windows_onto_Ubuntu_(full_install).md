---
title: "Can NOT install Windows onto Ubuntu (full install)"
date: 2018-01-13
forum: General Help
---

### Post by bozek74 on 2018-01-13
I just ordered a new Hard drive and decided I would try out the Ubuntu version of "Artful Aardvark" maybe its deemed as 17.10 or some such.. It seemed a valid way to get into things. I do not have a windows re installation disk. My computer is old and has a valid code sticker for Windows Vista Home Premium. 

So I hoped that Ubuntu/Linux/artful aadvark would be a great place to just start until I got things set up for a windows installation. Either finding a valid Vista Disk or a ISO file I could burn and work back towards a better Windows set up was on my back burner.. So I installed Ubuntu's Artful aardvark. Now I can't do anything but Linux.. I have a couple very old Windows XP disks that begin to try and set up but go to a blue screen during set up  and shut down saying its to "Prevent damage to my system"

I have downloaded and burned many other ISO images for Windows since.. Not a single copy on DVD or on USB will show as a bootable disk now. I have even tried doing this after installing my brand new Hard disk and same thing.. I get a Syslinux message Error: no blah blah UI or bootable disk whatever detected. So some how this Linux system is even still effecting my computer even with a blank brand new Hard disk and a copy of windows. 

I can only assume that Linux has made changes to my computer and somehow hijacked my RAM cards.. or some internal storage and will not allow Windows to do anything at this point. 

I have searched High and low and all I see is answers on how to dual boot linux and windows.. NONE of which work for me since windows wont even touch my computer with Linux now on it.. I need windows back as some of my hardware will not function with out Windows and I also enjoy many of Windows features like "playing some real games".

I have used other computers to burn the Windows disks and seen that they do indeed work until I put them in my computer and instead I just get that same notice.. Please Insert a bootable disk and strike any key to restart after they tell me that no configuration UI was detected. 

I actually did like many of Ubuntus features as being more logical but after all this I just want to get rid of Ubuntu and get back to windows.. But nothing has even remotely helped direct me towards doing this. Everything instead directs me to how to dual boot or install ubuntu. 

- My whole system is ubuntu..

- I need windows back (even if just partially)

- Ubuntu will not allow any Windows operations to complete. 

- Have played with boot sequence - has no effect

- Once Grub is touched which happens even with new Blank Harddisk installed it will not read any Windows product. 

Last note best progress I had was trying to use a very old hard copy of Windows XP which also fails but actually is recognized for a short time before it gets shut down to prevent damage to my system. 

If anyone can really help me with this you just became my hero.. Thank you for your time.

---

### Post by TheFu on 2018-01-13
Below are some dangerous commands which can wipe the entire HDD/SDD on any computer.  Only do this if you don't want any data from those disks, since it will be gone afterwards.

Some WinXP installations are tied to specific hardware. If the HW used doesn't match what the installer expects, then it refuses to work.  If the HDD is very large, older versions of Windows don't know what to do with it.  Hardware keeps moving forward, while unsupported OSes don't get those updates.

There is also UEFI booting (which WinXP doesn't support).  I think some version of Vista might have supported UEFI booting, but perhaps not the original.  This is a BIOS thing, so depending on the exact computer, UEFI might be included or not, enabled or not. If you didn't change any BIOS settings, then nothing has changed.

Linux didn't touch the RAM in a permanent way.  That isn't how operating systems work.

I cannot help with installing Windows. Haven't done that since 2010-ish. Sorry.

As for wiping the disks, you can wipe them a number of different ways (50+). This will destroy all the data, so don't do it if you want to keep any data.  You can use gparted, dd, ddrescue, gddrescue, dban, or almost any partitioning tool made for Linux, Widows, OSX, OS/2 or DOS.  Just delete all the partitions and zero out the partition table.  If you boot from an Ubuntu optical disc or flash drive, then open a terminal, you can type:
```
sudo dd if=/dev/zero of=/dev/sda bs=1M

``` This will wipe everything on the first HDD. DO NOT DO THIS if you want to retain any data from the drive. 
Leave it running overnight, though really 5 minutes should be more than enough to wipe the most important, first sectors. When you think it has been long enough, press **<cntl>-c** to stop the process. This will have effectively wiped the beginning of the disk with zeros.  For GPT disks, there will be another copy of the partition table at the other end of the disk.  GPT formatting has replaced MBR partitioning for many good reasons.  Vista support for GPT wasn't the best. I don't think XP supports it at all, but I'm hardly a MSFT expert.

v17.10 of Ubuntu really isn't something that new Ubuntu users should be using. It only has about 6 months of support remaining and includes some huge, complex, changes that might cause problems.  Go with 16.04.1 LTS or 16.04.3 LTS if you are new. Actually, 16.04 Gnome or Mate would probably be better, since the default GUI of the base version is not going to be the default GUI in the next LTS release this April.  Plus, any computer shipped with Vista probably has a lower-end GPU by the standards of today.  

Good luck.  If you don't have anything to loose, go crazy with the dd command.

Note: sda is almost always the first SATA device connected to a computer. If that isn't how it works on your system, it would be smart to post the text here from the **sudo parted -l** command run from a terminal.  /dev/sdb, /dev/sdc ...  /dev/sdz would be the 2nd, 3rd, ... disk in the computer, as the OS discovers them.  Sometimes that order changes at boot. That will show all the storage devices connected which are recognized.  It will show the optical disk or flash drive too.

Anyway, hope this is helpful.

---

### Post by RobGoss on 2018-01-13
First I would like to welcome you to the forums, There are tons of information on how to dual boot **Windows **and **Ubuntu** I always recommend on reading and getting familiar with the installation process before attempting to install Ubuntu . When dual booting Windows and Ubuntu, you should always make a full backup of your Windows partition and data just for safe keeping

Can you provide more information about your machine specs so others can help trouble shoot your problem. Did you install Ubuntu in **UEFI** or **Legacy? **

You should always have a recovery disk of any Windows OS you have installed before hand that way if something happens you can at least fix the broken Windows OS

Here's something that may help you have a better understanding how to dual your system 
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)  

Information on **UEFi**
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by grahammechanical on 2018-01-13
May I say that Ubuntu has not taken over your computer but only your hard disk. I am no expert on MIcrosoft Windows as I have not installed a version of it for a few years but, if I remember correctly, Windows will only install on a hard drive that has a Microsoft formatted file system. Linux/Ubuntu formats the hard drive to something called Ext4 by default and Windows does not recognize that as a valid file system.

I also understand that some old versions of Windows need to be first on the disk. Do these Windows install disks run in live mode like Ubuntu? If so you can use the Windows live mode to format the drive or a partition on it to a Windows format which may be FAT 32 or NTFS. I cannot say which one you should use for the version of Windows you wish to install.

As the Grub boot loader is on an early part of the drive you will need  to enter the BIOS/UEFI set up utility to direct the motherboard to look  for an OS on a DVD drive or USB stick. Whichever is appropriate.

I suggest that you think about formatting the drive to a Windows format  and then install Windows on to the whole drive and if you want to  continue with Ubuntu then install it as a dual boot system. Linux/Ubuntu  will install as a dual boot with Windows but Microsoft has not designed  Windows to dual boot with anything but a Microsoft OS.

You may also need to restore/fix the MBR to remove Grub and load Windows.

[https://neosmart.net/wiki/fix-mbr/](https://neosmart.net/wiki/fix-mbr/)

Regards

---

