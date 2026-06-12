---
title: "No boot loader for Windows after Ubuntu install?"
date: 2015-04-21
forum: General Help
---

### Post by jjmgray on 2015-04-21
Unable to start Windows after installing Ubuntu--I'm told that it fails to start, but repair can't seem to fix it and trying to start normally just bounces me back to the grub menu.

Ran boot repair and got this: [http://paste.ubuntu.com/10863743/](http://paste.ubuntu.com/10863743/)

I'm not sure why sda1 has ubuntu boot files, or why it seems to be formatted in FAT32.
Sda3 looks right, and the partition info seems right too.
I'm not seeing an error from the repair tool, but I need to get the Windows boot back.

Any ideas how should I correct this?


I've tried using the boot repair tool to reinstall the MBR for windows, but it only offers the option to fix the boot records in SDB, which isn't going to help me.

---

### Post by Vladlenin5000 on 2015-04-21
Hi and welcome.

Clearly you're unaware you previous Windows 7 is installed in UEFI mode (you installed Ubuntu in 'legacy' mode) and that's why you can't boot now: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) . Read this before attempting a dualboot in modern UEFI systems. First and foremost you need to understand UEFI - you don't; you wouldn't be asking about a FAT32 partition if you did).

PS - I hope you have good backups.

---

### Post by oldfred on 2015-04-21
Perhaps you booted Boot-Repair and it installed the efi version of grub to the efi partition on sda. 
It is not normal to have Ubuntu on sdb as MBR(msdos) partitioned and boot in UEFI mode.
Both Windows & Ubuntu normally install in UEFI mode to gpt partitioned drives.
And both only really boot in BIOS mode from MBR drives. But you have created an exception (that proves the rule?) as you have a BIOS install on sdb booting in UEFI mode using grub on the sda gpt drive's efi partition.
I am confused so you can be also. :)

As configured the only way you should boot is to go into UEFI/CSM and turn on UEFI and boot Windows. Then go into UEFI/BIOS turn off UEFI and/or turn on BIOS/CSM mode and change to boot sdb.  

How you boot install media and Boot-Repair is how it installs or repairs. You must have booted Boot-Repair in UEFI mode and it forced the install of grub-efi-amd64(UEFI boot) using efi partition on sda. It should have installed grub-pc(BIOS boot)to the MBR of sdb to boot Ubuntu.

---

### Post by jjmgray on 2015-04-22
My BIOS has a Legacy and UEFI option that I leave on.

I remember that I ran a LiveUSB of Ubuntu for Boot-Repair because it told me it couldn't do its work in a legacy mode of Ubuntu. Before that I didn't even have grub, I just booted directly to Ubuntu. Afterwards I had grub, but it couldn't load Windows.

Currently I've managed to resolve the issue by resetting the BIOS defaults, unplugging the sata cable from the Ubuntu HDD, and then using a restore point to get Windows functional again--the boot was apparently so broken that the /rebuildbcd command informed me that I had 0 Windows installations . . .
Guess I'll wait until this weekend and give it another shot.

I did a dual-boot once before with Linux Mint, but that was on one HDD with partitions, now I would prefer to just have two OS on two separate HDDs (I figured it would be simpler, shows what I know).


For the next installation I assume that this guide will work? [https://help.ubuntu.com/community/UEFI#Installing_Ubuntu_in_UEFI_mode](https://help.ubuntu.com/community/UEFI#Installing_Ubuntu_in_UEFI_mode)
Should I set the BIOS to be UEFI only? The files that I used to install Ubuntu before are on a FAT32 flash drive according to Windows, so they should be good for installing UEFI right?
Looks like I also had the boot wrong as well. At the time I just created a /boot. Apparently that should be a /boot/efi according to this: [https://help.ubuntu.com/community/UEFI#Creating_an_UEFI_partition](https://help.ubuntu.com/community/UEFI#Creating_an_UEFI_partition)
I think I also had the boot formatted as ext4 instead of FAT32.

All sorts of little things done wrong. :S
Oh well, live and learn I guess.

---

### Post by oldfred on 2015-04-22
If installing to a second drive I do suggest having the FAT32 formatted partition at beginning of the drive. To be an efi partition it must have boot flag. And you must partition with gpt, not MBR if using UEFI. With gparted you change to gpt before you start anything else.
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....I used

But grub will install to the efi partition on sda, even when during install it says installing to sdb. (That just happened to me, and it overwrote the ubuntu folder in my sda as I dual boot two Ubutnu installs).

New install should create new files in efi ubuntu folder. There is a three line grub.cfg that is a configfile to the real grub.cfg in your install. But that efi grub config must have the correct UUID, which if you reformat will change. New install should automatically do that.

The ESP or Efi System Partition is not Ubuntu's /boot. And with most desktop installs you do not need /boot in a separate partition. LVM or LVM with encryption do require a /boot or other server type installs may need a /boot.

The Ubuntu desktop installer is both UEFI & BIOS installer. How you boot installer is then how it installs. So be sure to boot in UEFI mode.

Some other guides essentially all the same as the one you have above. May be worth reviewing just to see them.
      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

 But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

