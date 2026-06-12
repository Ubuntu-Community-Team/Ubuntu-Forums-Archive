---
title: "Stuck at Grub Rescue unless USB drive (to which 12.10 was installed) attached."
date: 2013-03-29
forum: General Help
---

### Post by SuJ on 2013-03-29
I am on a Win7 laptop. I burnt a CD and installed Ubuntu 12.10 from it **to a drive connected by USB**.

I'm over my head on the Grub Rescue thing and assigning root. After watching several videos on YT I thought would help, I need to admit I need help.

I'd like to get to the "choose this or that partition menu" that happily comes up when the ext. drive is attached **without it being attached** (to clarify; if it's not, I get a Grub Rescue command) so I or my wife can go into Win7 or Ubuntu on a whim. I do have a HDD dock for secondary drive placement in lieu of the DVD drive on the way.

Scathing commentary as to why I installed to a USB drive instead of just tossing Win7 and / or doing things "in the right forsaken order" welcome. :)

Any good threads that address this or direction one could provide? I'm 24hrs into googling, video watching, and trying a couple minor things to try and fix this.

---

### Post by SuJ on 2013-03-29
log of what I've read:

[[ubuntu] My computer will no longer boot]("http://ubuntuforums.org/showthread.php?t=2129297&highlight=grub+rescue")
[[ubuntu] Windows 8/Ubuntu 12.10 dual install--boot repair issues]("http://ubuntuforums.org/showthread.php?t=2130433&highlight=grub+rescue")
[[ubuntu] Stuck at Grub Rescue unless USB drive (to which 12.10 was installed) attached.]("http://ubuntuforums.org/showthread.php?t=2130580&p=12579970#post12579970")
[[SOLVED] Ubuntu won't boot properly]("http://ubuntuforums.org/showthread.php?t=2130439")

---

### Post by oldfred on 2013-03-30
Did you do an auto install which installs the grub2 boot loader to sda (or internal drive)? But the grub in the MBR has to find the grub menu & rest of grub on the external drive?

If a new UEFI it may be a lot different on how to repair.

If BIOS.
Boot into Ubuntu with external. Double check that external is sdb, if not use that drive. Install grub to external.
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

    Then install a Windows boot loader to sda. (you can use Windows repairCD also.
       sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

    
Full instructions here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

This may automate process, or if you have Windows 8 pre-installed on internal drive, post link.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

If you do not have Windows repair.
      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Jay_E on 2013-03-30
Greetings,
I had problems when installing on PC with multiple drives.
There are  bugs.
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

I re-burned a DVD with Ubuntu Raring - 13.04 and it installed without a problem.

That said...
I have an uncomfortable feeling about  having your boot program set up to load ubuntu from a USB - which might not be there.  I'm not sure if the USB socket will make a difference - if you plugin into a different socket - or leave a different USB plugged in somewhere

If you are OK with YouTube, I'll say, "Grab a beer; watch videos on using  gparted to make some partitions on your hard disk; Install Ubuntu there."
(I like gparted live on a usb stick.)

About changing your hard drive and installing ubuntu as dual boot.
I have never had a problem with wiping out windows.
But that doesn't stop me from doing a clone disk.

About windows:
If you re-install windows, it will probably wipe out the Ubuntu partition.
[ Go ahead. Push my button. Ask why I don't like windows.]


You are doing great.
Sometimes it just takes a bit more patience.

Have fun,
Jay

---

### Post by SuJ on 2013-03-30
Thank you both for the high level of effort put into helping. I hope to digest and chip away at your suggestions in the coming week.

Jay, your post puts me at a column of reality. Not knowing my way around this stuff off my cuff means I'm spending hours to do what would take you & Fred 30min. Ultimately, I think a fresh install of both would make a lot of sense. For compatibility reasons for office and school work, I'll maintain some sort of Windows.

Have a great weekend, all.
J (not Jay) :)

---

### Post by oldfred on 2013-03-30
If installing to an external drive, it is important to use Something Else not any of the auto install options. All the auto install options install grub2's boot loader to sda which usually is the internal drive. At the bottom of the partitioning screen is a combo box on where to install grub2's boot loader. Usually you want sdb, and not any partitions like sdb1.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

I normally suggest a smaller system partition of 25GB and then a larger /home partition.

---

