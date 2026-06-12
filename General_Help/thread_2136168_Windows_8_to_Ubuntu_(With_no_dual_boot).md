---
title: "Windows 8 to Ubuntu (With no dual boot?)"
date: 2013-04-16
forum: General Help
---

### Post by cheekychap on 2013-04-16
Hey There!

This is my first post on here,
Im in a bit of a crumb.......I would like to know if it is possible and if anyone could help me but I want to completely switch from windows 8 to Ubuntu WITHOUT having to dual boot?

Is it possible to get it so that Ubuntu is just my complete Laptop OS.....without having the Dual boot screen at the start?
I really really really despise windows.....and from what I have used of ubuntu and linux in the past I freaking Loved it!

But Seriously if anyone at all could help I would appreciate it so much....Also my laptop was bought brand new with Windows 8 PREinstalled.....im sure there is a way? Also I do not have anything on my hard drive that I wish to save really as this is a new laptop. I have some documents already back up on a usb drive.....just awaiting instructions on how to make the big "Switch".

Thanks So Much,

CC

---

### Post by oldfred on 2013-04-16
Have you used Ubuntu before? 

Ubuntu is not Windows and new users really need to dual boot until they learn the differenences. I dual booted with XP for years as I has one application that was not as "good" in Ubuntu. The Linux equivalent got better and I realized I did not need all the features and now do not boot Windows.

At the very least Shrink Windows using Windows disk tools and make a full backup. Also backup efi partition. May be best not to overwrite the Vendor recovery partition which will occur with a install to entire disk option.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Linux is not Windows:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

   Ubuntu is not Windows
[http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/](http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/)
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

Some of the new UEFI systems have some things that make it more difficult or maybe impossible to totally eliminate Windows. Several users have done it, but it may depend you your specific hardware.

If you totally erase Windows you also have decide if you want UEFI or BIOS/CSM/Leacy boot. New systems now have the new UEFI in place of BIOS and with Windows 8 pre-installed have secure boot turned on. They also have a Windows/UEFI fast boot setting to make Windows boot quicker but if not turned off, you may not be able to get into UEFI/BIOS to boot.

This is for a UEFI install, but if you totally erase Windows you can install Ubuntu in BIOS/CSM/Legacy mode.

 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 

What computer is it? And is it an UltraBook? That makes it even more difficult but not impossible to install.

---

### Post by Rebelli0us on 2013-04-16
I [deleted Windows 8 from my new laptop]("http://ubuntuforums.org/showthread.php?t=2120763"). Just install Linux and tell the installer to delete all existing partitions. Some manufacturers have several partitions, boot, system, recovery, etc.

---

### Post by pqwoerituytrueiwoq on 2013-04-16
1st think i would do is disable secure boot in the bios so i don't need some binary blob from MS that gives the OS permission to boot on the system
just tell the installer to use the entire disk and it will replace windows, but make sure everything works on the live disk 1st (wifi, backlight, Ethernet, display)
it is recommened you backup windows or use a second hdd for ubuntu for warranty reasons from your systems manufacture

---

### Post by cheekychap on 2013-04-17
Thank you guys, I've spent most of my evening tinkering and just poking around BIOS and the like. I've tried Ubuntu and other forms such as mint and others in the past, But I'm new to BIOS and such. 
My Laptop is:
Packard Bell Easy Note TE 
Intel B830
4GB DDR3 Memory
500GB HDD
Preinstalled with Windows 8


I've come to the conclusion that I want to dual boot. For obvious reasons it makes much more sense as I might come across something down the line with College/Work that requires an OS other than a Linux based one. I have disabled Secure Boot.....but still cant get the USB to load. I even tried switching to Legacy but it would'nt even register a USB as being plugged in so I had to switch back. 

Newbie I know! 

Thanks Again.....but the fact that I can't even get the LiveUSB to register with BIOS is annoying me (well it does register but it says it wont allow it to happen).

Also I'm totally new to partitioning....i see I have 3....a recovery one (I think)....the regular one (the biggest with most of the GB's)....and another one.
So I dont know what I would do in that case to set up dual booting.....


Thanks Again....you guys rock!

CC

---

### Post by oldfred on 2013-04-17
Only new versions of 64 bit Ubuntu work with secure boot UEFI. With secure boot off, other newer distributions should work.
       Under Windows 8 Secure Boot, all PCs, no matter what operating system they actually run, must include several Microsoft-owned keys. 
 The State Of Linux Distributions Handling Secure Boot
[http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI](http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI)

Links in Post #2 show how to install with UEFI. You do have to have a good download, bootable flash drive and 64 bit. Also what video card/chip as that can cause some boot issues?

Be sure to use Windows Disk Tools to shrink the Windows partition but not to create any new partitions.

Do not know if Packard Bell is similar to parent co Acer or not in UEFI?
 Acer Windows 8 Video on getting into UEFI
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

---

### Post by cheekychap on 2013-04-17
Video Card is Intel(R) HD Graphics Family.......pretty crappy imo I know but Im a student on a Budget hehe!

Ok Im going to restart the whole operation....New LiveUSB and all.....so I will start with that and report on progress and any issues! Which USB Format/iso image loader would you guys reccomend?

---

### Post by oldfred on 2013-04-17
Many find this works:
 [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

      
 Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

---

### Post by Rebelli0us on 2013-04-17
Why not leave Win8 alone for now. How old is the laptop? Most newer laptops will boot off USB flash drive, but you may have to enter BIOS and set it as the boot device. If you can do that, then you can install Linux on a fast USB flash drive and boot from there while Windows stays as is on the hard disk.

---

### Post by oldfred on 2013-04-17
While you can do that, to dual boot you actually also have to install in UEFI mode to flash drive. Some have installed to second drives with gpt partitions and efi boot partition on second drive and dual booted.

It will work in BIOS mode from flash drive, but you have to go into UEFI/BIOS each time you change and turn on UEFI to boot Windows and turn off UEFI to boot a BIOS install. 

I highly recommend that any system with UEFI use gpt partitioning on all drives and even on flash drive if you may want to boot from it whether BIOS or UEFI. I only have BIOS but have a couple of flash drives with gpt partitioning and it works.

---

### Post by rikiriki on 2013-04-22
As far as I know, the firmware is unaffected and the block is virtually impossible to remove.

---

