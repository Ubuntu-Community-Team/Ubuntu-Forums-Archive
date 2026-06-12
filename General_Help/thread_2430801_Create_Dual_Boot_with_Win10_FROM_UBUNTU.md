---
title: "Create Dual Boot with Win10 FROM UBUNTU"
date: 2019-11-07
forum: General Help
---

### Post by THEKINGDOM on 2019-11-07
Hi guys,

So just about every single article or post out there is regarding those looking to make a dual boot **FROM Win10 to have Ubuntu** 
I run Ubuntu 18.04 as the primary, but unfortunately due to an app I need to run that's only available on Windows, I have no choice but to install Win10 on a dual boot, WINE isn't an option unfortunately. 

How would I go about **setting up a dual boot to Win10 from within Ubuntu 18.04**? (I have the Win10 .ISO) 
Also I have a 128GB SSD that's pretty full with Ubuntu plus installations. 


Shoud I:
[LIST]
[*]Just get another SSD for Windows entirely all together since the first is almost full?
[LIST]
[*]I guess a dual boot in this way would simply involve toggling between the boot drives on startup
[*]Coincidentally I have a GRUB screen showing on start-up issue, unresolved for over a year now (can't find a fix)
[/LIST]
[/LIST]

[B]OR
[/B]

[LIST]
[*]Find a way to upgrade to a larger SSD (eg 500GB) - clone existing SSD onto the new one and then partion?
[LIST]
[*]Does a partition drive have any advantages? Other than saving a drive slot?
[/LIST]
[/LIST]

Help is greatly appreciated. 

Thank you**&#8203;**

---

### Post by ajgreeny on 2019-11-07
If you need Windows 10 for just a single application I suggest you look at running a virtual install in, for example, VirtualBox.

There are other virtualisation applications available but I do not have experience of anything other than VirtualBox.
This will partly depend on your hardware having sufficient resources to run a VM but if the application you need it for is not too resource hungry and does not need full 3D acceleration from a graphic card, you should be OK.

---

### Post by THEKINGDOM on 2019-11-07
> **ajgreeny said:**
> If you need Windows 10 for just a single application I suggest you look at running a virtual install in, for example, VirtualBox.

There are other virtualisation applications available but I do not have experience of anything other than VirtualBox.
This will partly depend on your hardware having sufficient resources to run a VM but if the application you need it for is not too resource hungry and does not need full 3D acceleration from a graphic card, you should be OK.


Hi, thanks for the suggestions. The application I'm trying to run is actually a VR Fitness Game called Zwift, which is actaully fintastic by the way, used by many pro athletes as well. 
Unfortunately, based on reading and the resource demands of this game virtualization with VirtualBox has a few issues:
[https://forums.zwift.com/t/zwift-on-linux-on-virtualbox/5990/10](https://forums.zwift.com/t/zwift-on-linux-on-virtualbox/5990/10)
I'm also planning to run this to a 4K TV using a GTX 1070 or 1080 graphics card, not sure how that would work inside a virtual install

At this bottom of the above thead somebody noted that "[COLOR=#282828][FONT=Helvetica]wintousb" was working. But isn't that [/FONT][/COLOR][COLOR=#282828][FONT=Helvetica]basically [/FONT][/COLOR][COLOR=#282828][FONT=Helvetica]an "outside-system/external" dual-boot?[/FONT][/COLOR]

---

### Post by Frogs Hair on 2019-11-07
To start install gparted to handle creating the partitions. I have two Windows 10 dual boots with Ubuntu, but have never installed Windows from the Ubuntu side. Windows first was generally recommended when I started dual booting though it defiantly can be done.

---

### Post by Impavidus on 2019-11-07
Having Ubuntu and Windows on separate drives is better. It makes it less likely that Windows damages Ubuntu.

---

### Post by sdsurfer on 2019-11-07
^ I second that one, and it's nice to be able to swap them out when you need to. There are a couple extras you need to do for for Windows 10 that you don't in earlier versions, but it still works.

You would still need to configure grub for the boot process - you don't toggle the drives.

This is one of the guides I used to set up mine, it was fairly simple.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by crip720 on 2019-11-07
Depending on how full is pretty full, you should start thinking of a bigger drive anyway.  Used to be Win after Ubuntu gave minor problems, but with EFI seems to go okay, my limited experience and what I read.  Win can mess up Linux partitions on major upgrades if you are one of the unlucky ones, so having separate drives is good, if easy to remove one for upgrade.

---

### Post by THEKINGDOM on 2019-11-07
> **crip720 said:**
> Depending on how full is pretty full, you should start thinking of a bigger drive anyway.  Used to be Win after Ubuntu gave minor problems, but with EFI seems to go okay, my limited experience and what I read.  Win can mess up Linux partitions on major upgrades if you are one of the unlucky ones, so having separate drives is good, if easy to remove one for upgrade.

> **sdsurfer said:**
> ^ I second that one, and it's nice to be able to swap them out when you need to. There are a couple extras you need to do for for Windows 10 that you don't in earlier versions, but it still works.

You would still need to configure grub for the boot process - you don't toggle the drives.

This is one of the guides I used to set up mine, it was fairly simple.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

> **Impavidus said:**
> Having Ubuntu and Windows on separate drives is better. It makes it less likely that Windows damages Ubuntu.

> **Frogs Hair said:**
> To start install gparted to handle creating the partitions. I have two Windows 10 dual boots with Ubuntu, but have never installed Windows from the Ubuntu side. Windows first was generally recommended when I started dual booting though it defiantly can be done.

Thanks guys, I'll likely do separate drives then, tonight. 
How would I kick start the process to setup a new drive as the windows 10 OS - just load on the ISO and make that the boot drive?

Thanks

---

### Post by Skaperen on 2019-11-07
i know it costs more, but separate computers is the ultimate for having Linux and Windows together.  I've done this before and even had the two computers right next to each other and connected them to the same LAN.  they seemed to get along OK and neither did any damage or file corruption to the other.  you might not be able to do this right away, but planning it for the future might let you do it.  i know Ubuntu likes it when it doesn't have to reboot until the next kernel upgrade.

---

### Post by yancek on 2019-11-07
You might take a look at the Ubuntu documentation on dual booting with windows 10 at the site at the link below.  If you do windows EFI you should install Ubuntu EFI also or it will make the boot process more convoluted.  One problems with EFI is that Ubuntu will install Grub efi files to the first EFI partition it finds which could be the windows drive.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by tux-peng on 2019-11-07
I prefer separate drives as well; but if you use the same drive, maybe you should install grub to the root partition and use easybcd from within windows to chainload grub

---

### Post by THEKINGDOM on 2019-11-07
> **Skaperen said:**
> i know it costs more, but separate computers is the ultimate for having Linux and Windows together. I've done this before and even had the two computers right next to each other and connected them to the same LAN. they seemed to get along OK and neither did any damage or file corruption to the other. you might not be able to do this right away, but planning it for the future might let you do it. i know Ubuntu likes it when it doesn't have to reboot until the next kernel upgrade.

Why not just separate drives, rather than separate computers?

---

### Post by THEKINGDOM on 2019-11-07
> **tux-peng said:**
> I prefer separate drives as well; but if you use the same drive, maybe you should install grub to the root partition and use easybcd from within windows to chainload grub

I've just picked up an Intel SSD 660P-Series, 512GB for the Windows OS reside.

---

### Post by THEKINGDOM on 2019-11-07
> **yancek said:**
> You might take a look at the Ubuntu documentation on dual booting with windows 10 at the site at the link below.  If you do windows EFI you should install Ubuntu EFI also or it will make the boot process more convoluted.  One problems with EFI is that Ubuntu will install Grub efi files to the first EFI partition it finds which could be the windows drive.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

hmm okay. 
I've got the drive and the ISO for Win10. Ready to rock and roll.

We didn't quite establish how I can create a dual boot to WIn10 from a current Ubuntu OS. 
Can I just load the WIn10.ISO to the new drive and then  have window 10 install to that drive itself? If so, How would UEFI recognize the ISO?

Help is greatly appreciated

---

### Post by yancek on 2019-11-08
> We didn't quite establish how I can create a dual boot to WIn10 from a current Ubuntu OS. 

You can't boot and install windows from Ubuntu or any Linux system but you can create a bootable windows usb or DVD.  The link below gives a very detailed explanation of this using Ubuntu.  I'd read through the page before beginning following the steps and pay particular attention to the GPT/UEFI sections.  If you have Ubuntu UEFI, then you need windows UEFI.  If Ubuntu is Legacy/CSM, then windows needs to be the same.  If the drive you will use for windows is GPT, you must install windows UEFI.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)


If you use the UEFI method, you should see an option on booting the computer in the BIOS/firmwate to select the usb drive with the 'UEFI' in the option.

---

### Post by oldfred on 2019-11-08
I do not know about UEFI install of Windows, but with BIOS version you have to be careful on drives.

And be sure to have good backups before any major system change.

Windows will install its boot loader to drive seen as default boot in BIOS.
Some install Windows to sdb drive and it has a small boot partition on sda. Users have deleted that boot partition and broken Windows.
Have also seen cases where Windows install just arbitrarily put boot partition on sda, overwriting the start of a Linux partition damaging Ubuntu.

If newer system better to use UEFI, but as yancek says you want both Ubuntu & Windows in same boot mode, both UEFI or both BIOS.

Whether UEFI or BIOS, better to disconnect, either physically or with settings in UEFI to make inactive, so Windows installer only sees new drive.
You may lose UEFI entry for Ubuntu, but can easily recreate with Boot-Repair or efibootmgr. Many systems lose UEFI entries when drive is removed.
And if Windows fast start up is off, you can in Ubuntu run this to chainload in grub to boot Windows.
sudo update-grub

---

### Post by yancek on 2019-11-08
Windows 10 has a "Custom" installation option which you should see just after the page with the EULA.  I used this on a Legacy machine to install windows 10 to an already existing ntfs partition and the only problem was that windows overwrote the boot code in the MBR.  That was an easy fix.  I'm not sure what happens with an EFI system but I would expect you would be able to do something similar as windows creates separate directories for its EFI files on the EFI partition.  That's just a guess as I have not done it myself.

---

### Post by THEKINGDOM on 2019-11-09
Attached boot repair log: 
[http://paste.ubuntu.com/p/9WjWk2smF5/](http://paste.ubuntu.com/p/9WjWk2smF5/)

Not quite sure if I'm on UEFI or not on the boot drive - [COLOR=#000000]/dev/nvme0n1p4
Want to be on UEFI before I attempt to install Win10 OS to a separate M.2-SSD

FYI in the above log - sda & sdb are my ZFS data RAID - shouldn't be anything to do with boot. 
I've just moved over from AMD back to Intel today. It seems as if the dredded GRUB screen is now appearing again on every boot and I'm not sure why. Is there any issue with having non-boot drives in SATA slots 1 & 2?

Any  help is greatly appreciated 


[/COLOR]

---

### Post by yancek on 2019-11-09
> Not quite sure if I'm on UEFI or not on the boot drive - [COLOR=#000000]/dev/nvme0n1p4[/COLOR]

That would be the system partition on which you have your Ubuntu install.  Take a look at the boot repair file, line 110 shows:

> /dev/nvme0n1p1   308D-E09D                              vfat 

The vfat would indicate your EFI partition.  Look at line 211 which clearly shows an EFI partition.

> /dev/nvme0n1p1: UUID="308D-E09D" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="ec4290d6-24a0-4b3f-924f-c4605c52ca57"

Since the disk on which you have Ubuntu and want to also install windows is GPT (see line 703 of boot repair), that means you must install windows UEFI.  Also, on line 707, your EFI partition is shown and on line 708 it shows BIOS boot partition.  You do not need this as the BIOS boot partition is used only for a non-UEFI install on a GPT partition with Linux.  You might want to disable Legacy/CSM boot in the BIOS firmware before installing.  Line 709 shows you have a swap partition and newer versions of Ubuntu do not use/need a swap partition but rather a swap file so this is also probably not needed but should not hurt anything, other than using up space.  32GB is much more than necessary.  If you add up the space used for the partitions on the SSD, they come out to approximately the full size of the drive so there is no place on which to install windows.  You need an ntfs partition for windows and 30GB is probably the bare minimum necessary. 

Just read over your previous posts.  Have you got a 2nd drive for windows?  That would eliminate the size problem on the above drive.  If you do have another drive, after burning your windows iso to a DVD or putting it on a USB, it would probably simplify things if you were able to dis-connect the Ubuntu SSD so it is not overwritten.  That would lead to another possible problem with multiple EFI partitions, one on the Ubuntu drive and one on the windows.  That should not be that difficult to resolve.

I'd suggest again, reading through the Ubuntu documentation on dual booting with windows 10 UEFI.

---

### Post by oldfred on 2019-11-09
While you have the ESP, if you also have a bios_grub you must have installed in both modes or converted install.
Boot-Repair seems to want to reinstall grub in BIOS boot mode.
Report also did not show /etc/fstab which would show if ESP is mounted or not. Reinstall of grub in BIOS mode would comment it out with #.

Saw a post where user was having issue and it related to the ZFS being set as back up boot in UEFI settings causing issues.
Post by THEKINGDOM :)
[https://ubuntuforums.org/showthread.php?t=2406222&p=13904610#post13904610](https://ubuntuforums.org/showthread.php?t=2406222&p=13904610#post13904610)

Post this, since missing from report:
cat /etc/fstab

---

### Post by THEKINGDOM on 2019-11-09
> **yancek said:**
> That would be the system partition on which you have your Ubuntu install.  Take a look at the boot repair file, line 110 shows:



The vfat would indicate your EFI partition.  Look at line 211 which clearly shows an EFI partition.



Since the disk on which you have Ubuntu and want to also install windows is GPT (see line 703 of boot repair), that means you must install windows UEFI.  Also, on line 707, your EFI partition is shown and on line 708 it shows BIOS boot partition.  You do not need this as the BIOS boot partition is used only for a non-UEFI install on a GPT partition with Linux.  You might want to disable Legacy/CSM boot in the BIOS firmware before installing.  Line 709 shows you have a swap partition and newer versions of Ubuntu do not use/need a swap partition but rather a swap file so this is also probably not needed but should not hurt anything, other than using up space.  32GB is much more than necessary.  If you add up the space used for the partitions on the SSD, they come out to approximately the full size of the drive so there is no place on which to install windows.  You need an ntfs partition for windows and 30GB is probably the bare minimum necessary. 

Just read over your previous posts.  Have you got a 2nd drive for windows?  That would eliminate the size problem on the above drive.  If you do have another drive, after burning your windows iso to a DVD or putting it on a USB, it would probably simplify things if you were able to dis-connect the Ubuntu SSD so it is not overwritten.  That would lead to another possible problem with multiple EFI partitions, one on the Ubuntu drive and one on the windows.  That should not be that difficult to resolve.

I'd suggest again, reading through the Ubuntu documentation on dual booting with windows 10 UEFI.

Thanks yancek. Indeed, I have another 512GB M.2 SSD dedicate for Win10 as I want to stay away from partitioned drive for Dual-Boot. So the drive size issue is solved. 
I'll also be sure to remove the Ubuntu drive for safety when installing win10. 

You mentioned: >  "Your EFI partition is shown and on line 708 it shows BIOS boot partition. You do not need this as the BIOS boot partition is used only for a non-UEFI install on a GPT partition with Linux." 
[LIST]
[*]Is UEFI or EFI essentially the same thing?
[*]Do I have the correct boot configuration to have a dual boot on UEFI for Win10?
[*]Does it appear that I have **both** EFI & Bios partitions? (as referenced by **oldfred) **Or am I confused? Sorry
[/LIST]

Thanks

---

### Post by THEKINGDOM on 2019-11-09
> **oldfred said:**
> While you have the ESP, if you also have a bios_grub you must have installed in both modes or converted install.
Boot-Repair seems to want to reinstall grub in BIOS boot mode.
Report also did not show /etc/fstab which would show if ESP is mounted or not. Reinstall of grub in BIOS mode would comment it out with #.

Saw a post where user was having issue and it related to the ZFS being set as back up boot in UEFI settings causing issues.
Post by THEKINGDOM :)
[https://ubuntuforums.org/showthread.php?t=2406222&p=13904610#post13904610](https://ubuntuforums.org/showthread.php?t=2406222&p=13904610#post13904610)

Post this, since missing from report:
cat /etc/fstab

[COLOR=#000000]**cat /etc/fstab**# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p4 during installation
UUID=43fbccca-d567-442c-a9f6-1f2f855ff259 /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0

> if you also have a bios_grub you must have installed in both modes or converted install.
Does this mean I can just delete the GRUB2 parition and my situation would be solved?



[/COLOR]

---

### Post by oldfred on 2019-11-09
No, you have to boot Boot-Repair in UEFI boot mode and in Advanced mode do the total reinstall of grub. You want to install grub-efi-amd64, not the BIOS version grub-pc. It may not say exact version, but you just want UEFI install.

How you boot install or repair media UEFI or BIOS is generally how it installs or repairs your installed system. You normally have two boot modes UEFI or BIOS for USB flash drive if UEFI Secure Boot is off. But then you also have to have UEFI set to boot in that boot mode for installed system. Some UEFI are more clear than others on settings. One of my systems will only boot in BIOS mode, if set for UEFI or BIOS. But if UEFI only then UEFI works just fine.

Your fstab does not show mount of ESP. This is mine with my UUID, so you cannot use it, its just an example of what you should see if UEFI boot installed.
I also comment out original install & change to defaults. Boot-Repair also does this. Ubuntu used defaults back before 14.04 or abouts. I think they changed to umask=0077 for secuity to prevent any write into FAT32 partition when booted.

```
#UUID=D966-440A  /boot/efi       vfat    umask=0077      0       1
UUID=D966-440A  /boot/efi       vfat    defaults      0       1

```

EFI was the original release of a new replacement for PC BIOS from 1980's by Intel. It was adopted by Apple when they converted to Intel chips. Intel then turned it over and it became UEFI v2 and EFI then became UEFI v1. Microsoft then adopted UEFI as its standard in 2012 for all pre-installed Windows. originally they were not going to allow BIOS installs, but many large companies did not want all new computers but then needed BIOS install. So a user can install in the old BIOS/MBR boot mode, but probably should not if hardware is newer.
[https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by THEKINGDOM on 2019-11-09
>  You want to install grub-[COLOR=#ff0000]efi-amd64[/COLOR], not the BIOS version grub-pc. It may not say exact version, but you just want UEFI install. 
I've switch MOBO & CPU to Intel - I've just moved away from AMD

>  No, you have to boot Boot-Repair in UEFI boot mode and in Advanced mode do the total reinstall of grub 

[LIST]
[*]Should I be checking the box "Separate /boot/efi partition"?
[*]What do I need to do in order to get my boot partition to be UEFI?
[/LIST]
[ATTACH=CONFIG]284365[/ATTACH]

>  How you boot install or repair media UEFI or BIOS is generally how it installs or repairs your installed system. You normally have two boot modes UEFI or BIOS for USB flash drive if UEFI Secure Boot is off 
[LIST]
[*]Do I have to have secure boot enabled in order to boot into UEFI?
[/LIST]

I've tried swtiching the MSI-Bios to **UEFI boot only** instead of **UEFI/Legacy** and what happens is that it just bounces me between GRUB2 screen to BIOS and back again, each time I reboot I can't boot ubuntu unless I go back into Bios and change to **UEFI/Legacy - **would this give any clue as to what is happening?

Sorry but there's a lot of confusion and back and forth, I really do appreciate all the info and help.
All I'm trying to understand is - How can I get my current system to be UEFI boot only and thus ready for a side by side dual-boot with Win10 -** separate drives**. If I could give me a basic 3 or so steps I'll execute right now. 


Thanks

---

### Post by oldfred on 2019-11-09
It looks like you installed grub in BIOS boot mode. So system only boots in BIOS boot mode.
So in UEFI boot mode, you do not get anything.
But you still should be able to boot flash drive in UEFI boot mode. Then reinstall grub, so system can boot in UEFI boot mode.
Is the screen you show from Boot-Repair booted in UEFI mode. I thought it then auto checked the separate efi partition box.
Maybe in BIOS mode, it will let you install UEFI version of grub, if you check box? Do not know.

There really are three boot modes. UEFI with Secure boot, UEFI (without secure boot), and BIOS/CSM/Legacy. With secure boot off, you get both UEFI & BIOS, but system may default to one or the other. Probably better to have UEFI only. But when booting flash drive, you still have to select the UEFI:flash not flash entry, where flash is name or label of flash drive. Mine is UEFI:PMAP & PMAP. I only boot UEFI:PMAP for flash drives.

Does FAT32 partition have boot flag? That is how gparted/parted set a FAT32 partition to be the ESP - efi system partition. You can only have one ESP per device, but can have multiple FAT32 (although FAT32 not recommended for larger partitions, better to use Linux formats for Linux anyway).

Update:
These are the UEFI settings I have on Asus. You may have similar UEFI settings, but each vendor does it somewhat differently.
Asus-ar screenshots oldfred
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by THEKINGDOM on 2019-11-09
> **oldfred said:**
> It looks like you installed grub in BIOS boot mode. So system only boots in BIOS boot mode.
So in UEFI boot mode, you do not get anything.
But you still should be able to boot flash drive in UEFI boot mode. Then reinstall grub, so system can boot in UEFI boot mode.
Is the screen you show from Boot-Repair booted in UEFI mode. I thought it then auto checked the separate efi partition box.
Maybe in BIOS mode, it will let you install UEFI version of grub, if you check box? Do not know.

There really are three boot modes. UEFI with Secure boot, UEFI (without secure boot), and BIOS/CSM/Legacy. With secure boot off, you get both UEFI & BIOS, but system may default to one or the other. Probably better to have UEFI only. But when booting flash drive, you still have to select the UEFI:flash not flash entry, where flash is name or label of flash drive. Mine is UEFI:PMAP & PMAP. I only boot UEFI:PMAP for flash drives.

**Does FAT32 partition have boot flag?** That is how gparted/parted set a FAT32 partition to be the ESP - efi system partition. You can only have one ESP per device, but can have multiple FAT32 (although FAT32 not recommended for larger partitions, better to use Linux formats for Linux anyway).

Update:
These are the UEFI settings I have on Asus. You may have similar UEFI settings, but each vendor does it somewhat differently.
Asus-ar screenshots oldfred
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

[ATTACH=CONFIG]284368[/ATTACH]

Yes, there is a Boot flag on the FAT32 

> Is the screen you show from Boot-Repair booted in UEFI mode. I thought it then auto checked the separate efi partition box.
Maybe in BIOS mode, it will let you install UEFI version of grub, if you check box? Do not know. 
Here's what happens if I tried to check the box for UEFI partition - 
[ATTACH=CONFIG]284369[/ATTACH]

So I should: 
[LIST=1]
[*]Create a Ubuntu flash drive and boot with UEFI - would this be the same as a Ubuntu Live drive?
[*]Select UEFI:Flash
[*]Reinstall GRUB
[/LIST]

---

### Post by oldfred on 2019-11-09
Ubuntu live installer is both BIOS & UEFI.

But some installer software may create it one way or the other. Just verify if you can boot in UEFI mode from UEFI boot menu. 
Or recreate installer making sure settings are for UEFI.

---

### Post by THEKINGDOM on 2019-11-09
> **oldfred said:**
> Ubuntu live installer is both BIOS & UEFI.

But some installer software may create it one way or the other. Just verify if you can boot in UEFI mode from UEFI boot menu. 
Or recreate installer making sure settings are for UEFI.

ok so are you suggesting I don't use Ubuntu live installer via UNetBootin? 
If not, then what do I need to make? A full Ubuntu 18.04 flash drive? As if I was going to flash Ubuntu fresh?
If so, with which installer do you suggest? 
I can't determine what you mean, sorry

---

### Post by oldfred on 2019-11-09
I have this in my notes, not sure if still current:
not updated, only very new ppa version as of Aug 2015
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

And someone posted that one of the installer offered to make either UEFI or BIOS install flash drives, even though ISO is configured for both.

Also link on how to create a  bootable DVD or USB flash drive, using Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) or 
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Updates for ISO to USB.
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)
Updates -Instructions to make a boot drive, that boots both in UEFI and BIOS mode
[https://help.ubuntu.com/community/Installation/iso2usb/diy](https://help.ubuntu.com/community/Installation/iso2usb/diy)
[https://ubuntuforums.org/showthread.php?t=2299040](https://ubuntuforums.org/showthread.php?t=2299040)

Have not used an installer for ages, but my method requires Ubuntu/grub and grub's loopmount boot of ISO directly.

---

### Post by THEKINGDOM on 2019-11-09
Hi oldfred, I know how to make a ubuntu flash/boot drive. 
My question was pertaining strictly being able to correct my existing Ubuntu OS boot partition to make it **UEFI** **ONLY** before I perform my install of Win10 for dual-boot (separate drives). 
Can you please clarify what I need to do??

I'm creating a **boot drive-USB** right now with the latest 18.04 LTS Ubuntu. I'm going to boot into this drive and hope to correct EXISTING boot partition to UEFI? 
**RESULT**: _**didn't work.**_ The bootable USB made me boot in Legacy and therefore I still can't repair the boot partition to UEFI. 


**Update:**
Re-attemping one last time to see if I can boot this USB in EFI/UEFI
Formatted Volume to FAT32 & GPT Partition
Using Unetbootin to install 18.04

---

### Post by THEKINGDOM on 2019-11-09
**UPDATE: **

It looks like it might have worked with FAT32/GPT

**Please see below Gparted Disk info **
[ATTACH=CONFIG]284370[/ATTACH]


**Below Boot-Info pastebin:**

[http://paste.ubuntu.com/p/b434vqZyF2/](http://paste.ubuntu.com/p/b434vqZyF2/)



[LIST]
[*]Does anything look out of place here?
[*]Or have we fully converted my bootloader environment from BIOS to UEFI/EFI?
[*]Is it safe now to start my Win10 install (separate disk)  - chosing UEFI as the bootloader enviornment?
[/LIST]

---

### Post by oldfred on 2019-11-09
Report still does not show fstab?
But you now have an Ubuntu entry in your UEFI as a boot option. from sudo efibootmgr -v
All Boot-Repair really does for report is run a lot of standard commands & then put them together into report.

You do not have to have swap partition, but that is ok.
New versions of Ubuntu now use swap file, but will use swap partition if you already have one.
Also swap does not have to be large if you have a lot of RAM. My old BIOS system with 4GB of RAM did not use swap with my normal use. If edition videos or loading every app and lots of tabs in a browser, you may use swap, but even that may not.

---

