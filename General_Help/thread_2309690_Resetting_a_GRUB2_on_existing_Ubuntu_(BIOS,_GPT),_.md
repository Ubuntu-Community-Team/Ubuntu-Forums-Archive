---
title: "Resetting a GRUB2 on existing Ubuntu (BIOS, GPT), that Boot-Repair fails to fix."
date: 2016-01-12
forum: General Help
---

### Post by lb.rudewolf on 2016-01-12
Hello to whoever crosses this lines,

I have issues in fixing a Grub2 on my laptop.

Any advice appreciated.

PS: It happens to be my first post on the forum. So hi to the forumers.

--------------------------------
[B]
For the context[/B] (you may skip tis part)
My laptop is a Thinkpad X220 which comes with two hard drives
[LIST=1]
[*]A internal micro SSD one;
[*]A main hard-drive (internal to, but easier to access)
[/LIST]
Recently I had a failure on the microSSD, which contains the pre-installed
Windows system, the messy OEM partitions, etc. I have yet to determine
if I ll be able to recover anything from it. That the kind of **** which can happen :(.
My warranty still works for a few more months, which entitles me with a replacement
of piece (the drive, not the data) and maybe the motherboard (the failure 
happened related to a likely power issue, better not have anything else burn).

**In short**: I sadly lost a drive (most likely).

**Issue**
This drive at fault also contained my boot-loader, an instance of GRUB2.
I am faced with setting up a new a bootloading setting based on my other drive:
I will call it *the main drive*. On this main drive, I still have my main Linux (ubuntu) 
system and I wish to get back access to it.Since I last dwelved into the GRUB/GRUB2 thingies, standards have evolved quite
some, and I must admit It gets me quite confused, how to adapt GRUB2 to my situation.
[LIST]
[*]Informed answers/confirmations to questions below are especially sought.
[/LIST]
I booted a Boot-Repair-Disk USB key with te objective to one-click fix my Grub, to no 
success so far: My BIOS/EFI still won't boot my main drive (no access to GRUB on it). 
Anyway, after I wil have got my hands on a replacement micro SSD, I will need to setup
my dual boot again. So I'd better get acquaited with up to date GRUB2 setup.
  
**Setup**
For once my main drive partition scheme has since evolved to GPT, and I think that 
is the reason why I chose to place GRUB2 on the other drive instead.
[LIST]
[*]Is it true that I will need a BIOS-GRUB partition of a few unformated MB?
[/LIST]
My Ubuntu, already installed (and that I wish to keep safe out of the business,) seems
 to be installed in the BIOS/Legacy scheme instead of EFI. 
My computer BIOS/EFI seems to be able to work in both BIOS and EFI mode 
(one; or the other; or both with a preference for one). This raises a few questions.

[LIST]
[*]Is it true that I should setup my BIOS/EFI on the BIOS setting?
[*]Optional: Should I call it an EFI ? Or is it an EFI-capable BIOS? (I ll keep on with calling it BIOS/EFI for now)
[LIST]
[*]**edit: **this is an (U)EFI, which can emulate a BIOS (also known as CSM: [https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Compatibility_Support_Module](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Compatibility_Support_Module) ; see also [http://www.rodsbooks.com/gdisk/booting.html](http://www.rodsbooks.com/gdisk/booting.html) )
[/LIST]

[*]I think I figured this one out, but for the sake anyone out there: how would you determine if an existent Ubuntu is EFI or BIOS?
[LIST]
[*]**edit**: see [https://help.ubuntu.com/community/UEFI#Identifying_if_an_Ubuntu_has_been_installed_in_UEFI_mode](https://help.ubuntu.com/community/UEFI#Identifying_if_an_Ubuntu_has_been_installed_in_UEFI_mode)
[/LIST]
[/LIST]

**To summarize:** 
I'm trying to setup a GRUB2 on a GPT drive for a preexisting BIOS Ubuntu system on 
a BIOS/EFI capable laptop. Boot-Repair failed to help. It seems that it Installed GRUB2
on the the drive (sda), but I could not boot my laptop on it.
For those interested, here is a latest Boot-Info report:
[http://paste.ubuntu.com/14480341/](http://paste.ubuntu.com/14480341/)
[LIST]
[*]In a GPT scheme is GRUB2 installed in the MBR ?
[LIST]
[*]**edit:** If a picture is worth thousands words, see [https://en.wikipedia.org/wiki/BIOS_boot_partition](https://en.wikipedia.org/wiki/BIOS_boot_partition) .
[/LIST]
[/LIST]

**So far**
So far I managed to boot my Ubuntu once. I booted on the USB Boot-Repair-Disk,
in laptop's EFI mode (don't know why it is involved). From its GRUB menu, I entered in
command line. (The GRUB from the USB stick, my issue is I have not yet succeeded in
booting the GRUB from the drive). From GRUB command line I could load and boot my 
Ubuntu system, with something like these four GRUB console commands (out of memory):
```

set root=(hd1,gpt3)
linux /boot/vmlinuzSOMENUMBER root=/dev/sda3
initrd /boot/initrdSOMENUMBER
boot

```

Thanks to IBM/Lenovo helpline, I could not avoid to reboot the computer.
(They wished to be sure of the serial number for warranty status, and the
sticker they put did not pass te years, so they had to have me go to the BIOS/EFI
setup interface...)
[B]
Another issue[/B]
[LIST]
[*]I could not successfully complete Ubuntu boot since.
[/LIST]
In the booting process of Ubuntu, from manual GRUB usage, I am since then
stuck at ''initramfs recovery console'' (or watever the name). It seems to fail mounting
mz sdax, including the root partition and cannot find /etc/fstab. (that I duly cleaned of
references to the now defect and removed micro SSD drive).

**Extra**
My main drive happen to be of a specific type. It is a hybrid SSD/HDD drive of
Western Digital (a Black2) that I indulged as an upgrade. Due to lack of Linux support 
at the time, I only partitioned it in one drive. I hope the specific nature of the drive won't
impede the booting process.

---

### Post by Seanan on 2016-01-12
This post is somewhat confusing so just to help clarify, you are trying to install grub bootloader on the same drive as your ubuntu installation that did not have grub already on it?

---

### Post by grahammechanical on 2016-01-12
It is difficult to know how to answer the issues you have raised. Which are not necessarily related to the main problem of not being able to load Ubuntu. And so are a distraction.

GPT = GUID Partition Table. Globally Unique Identifier = GUID. This is part of the UEFI standard. If we have a motherboard that has a UEFI boot system and not BIOS boot system we can install Ubuntu in either EFI mode or BIOS/Legacy/Compatibility mode.

If Ubuntu is the only OS then it does not matter which mode we install Ubuntu in. But If Ubuntu is going to be installed with Microsoft Windows pre-installed then we need to install Ubuntu in the same mode that Windows is installed in. Otherwise we will only be able to load one of the OS. 

If we run the live session in EFI mode then Ubuntu will install in EFI mode. If we run the live session in BIOS/Legacy mode then Ubuntu will be installed in BIOS/Legacy mode.

Microsoft Windows 8/10 are pre-installed in EFI mode.

With an UEFI boot system we usually get GPT. An OS installed in EFI mode on GPT partitioned disks will need a EFI boot partition for the boot files. An OS installed in BIOS/Legacy mode on GPT partitioned disks will need bios boot partition. The Ubuntu installer can automatically take care of that.

Windows pre-installed in EFI will already have an efi boot partition that the Ubuntu installer can use without affecting the Windows boot files in the partition.

Look at the boot repair info summary at sda3 Do you see this?
> 
File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 15.04 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img


Ubuntu is installed in BIOS/Legacy mode.

This is the kind of thing we see if both Windows and Ubuntu are installed in EFI mode. Note the Ubuntu related EFI boot files.
> 
 File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bkpbootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi

According to the Boot Repair Info summary you did not accept the offer to re-install Grub 2 into the MBR of sda3
> 
=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda3 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s


=================== User settings
The settings chosen by the user will not act on the boot.


As a guess in the dark, have you entered the UEFI boot system and directed the motherboard to load from what is now sda? Or is the motherboard still looking to the failed microSSD? It might also be a case of the manufacturer setting up the hardware to only boot from the SSD? Have you thought of that?

Regards.

---

### Post by lb.rudewolf on 2016-01-12
''you are trying to install grub bootloader on the same drive as your ubuntu installation that did not have grub already on it?''
Exactly. That is my starting issue.

I tried to install Grub on this drive through Boot-Repair. Boot-Repair says it did the job: it exits without error and suggests to try a reboot.
Nevertheless, I have been enable to activate this purposedly installed GRUB.

---

### Post by lb.rudewolf on 2016-01-12
> **grahammechanical said:**
> It is difficult to know how to answer the issues you have raised. Which are not necessarily related to the main problem of not being able to load Ubuntu. And so are a distraction.

GPT = GUID Partition Table. Globally Unique Identifier = GUID. This is part of the UEFI standard. If we have a motherboard that has a UEFI boot system and not BIOS boot system we can install Ubuntu in either EFI mode or BIOS/Legacy/Compatibility mode.

If Ubuntu is the only OS then it does not matter which mode we install Ubuntu in. But If Ubuntu is going to be installed with Microsoft Windows pre-installed then we need to install Ubuntu in the same mode that Windows is installed in. Otherwise we will only be able to load one of the OS. 

If we run the live session in EFI mode then Ubuntu will install in EFI mode. If we run the live session in BIOS/Legacy mode then Ubuntu will be installed in BIOS/Legacy mode.

I have an already installed an Ubuntu system. I think it is an BIOS/Legacy one. Maybe because it had to dual boot with a Windows 7. Maybe because
it is a very old one (at least 5 years, it has undergone many versions upgrades). I am running a Boot-repair-disk, based on a modified live (L)ubuntu.
My laptop can boot both EFI and BIOS/Legacy. As an interrogation, I don't clearly understand whether booting Boot-repair in UEFI or BIOS does impact
its functions: will it be able to install GRUB in one mode only?

> **grahammechanical said:**
> 
Microsoft Windows 8/10 are pre-installed in EFI mode.

In my case my former Windows was a Windows 10, but an upgrade from a preinstalled Windows 7. It seems to me my system was booting in BIOS mode.

> **grahammechanical said:**
> 
With an UEFI boot system we usually get GPT. An OS installed in EFI mode on GPT partitioned disks will need a EFI boot partition for the boot files. An OS installed in BIOS/Legacy mode on GPT partitioned disks will need bios boot partition.

Thanks for clarifying that. 

My Ubuntu is on a GPT drive. I did not have any EFI boot. I did not have a bios boot partition. Rather I booted from a GRUB on the other drive,
the regretted drive, which was not a GPT, but used the old MBR partitioning (from the OEM). According to zour quote, in order to boot from a 
GRUB on the GPT drive, I need to make a bios boot partition. I did this, following boot-repair instructions: a small few MB unformated partition 
with the bios-grub flag on it. With such a partition Boot-repair was able to terminate. Even though, I could not boot the grub It claimed to have
set up.

> **grahammechanical said:**
> 
The Ubuntu installer can automatically take care of that.

Speaking for myself, I would prefer to recover my former system, rather than install a new one.

> **grahammechanical said:**
> 
Look at the boot repair info summary at sda3 Do you see this?

Ubuntu is installed in BIOS/Legacy mode.


> **grahammechanical said:**
> 
This is the kind of thing we see if both Windows and Ubuntu are installed in EFI mode. Note the Ubuntu related EFI boot files.

You got me quite confused here. I thought you were talking about BIOS/Legacy.

> **grahammechanical said:**
> 
According to the Boot Repair Info summary you did not accept the offer to re-install Grub 2 into the MBR of sda3
 
If you are referring to this, I think it is because the report was generated Boot-info only,
not boot-repair. I had tried the repair tool several times already, the automatic repair:
It seems to me that these repairs action was to move the GRUB from the sda3 to sda.
> **grahammechanical said:**
> 
=================== User settings
The settings chosen by the user will not act on the boot.





> **grahammechanical said:**
> 
As a guess in the dark, have you entered the UEFI boot system and directed the motherboard to load from what is now sda? Or is the motherboard still looking to the failed microSSD? It might also be a case of the manufacturer setting up the hardware to only boot from the SSD? Have you thought of that?

Regards.
From the UEFI Boot system, I chose the BIOS/legacy setting (I had tried the UEFI too). I set the boot order on the functioning drive.
For simplicity I had the defective drive entirely removed from the system (physically: screwdrive open the laptop, etc...). The motherboard
is not concerned anymore with the micro SSD.
The manufacter did not lock the boot. I don't believe it shall be Lenovo/thinkpad policy, and in the past I did boot on the other drive
(which at the time was the manufacturer drive, and was not GPT; the current drive and partitioning scheme arose when I upgraded
this drive).

Thanks for the help.

---

### Post by oldfred on 2016-01-12
In BIOS boot mode from UEFI/BIOS you should be able to boot the hard drive in BIOS mode.
You must have UEFI off, secure boot will be off as BIOS mode has no secure boot and have Legacy/CSM/BIOS mode on.
It looks like it should boot in BIOS mode. Grub is installed in MBR, which is standard for BIOS even with gpt partitioning.

You do have a lot of kernels. Time to houseclean once you get it working.

---

### Post by lb.rudewolf on 2016-01-14
> **oldfred said:**
> In BIOS boot mode from UEFI/BIOS you should be able to boot the hard drive in BIOS mode.
You must have UEFI off, secure boot will be off as BIOS mode has no secure boot and have Legacy/CSM/BIOS mode on.

I did not yet document myself on these Secure Boot issues. For now I am trying to successfully set up a BIOS Grub2 GPT
booting. I still have the option to try an (U)EFI Grub2 GPT booting, but I might have to tweak my installed Ubuntu, which
I would leave it as a further resort.

> **oldfred said:**
> 
It looks like it should boot in BIOS mode. Grub is installed in MBR, which is standard for BIOS even with gpt partitioning.

Thanks for this info. I have trying to check manually my GRUB2 installation. So far I could detect on the "grub_bios" flaged
partition I created, in its first 512 bytes, a copy of GRB2's "diskboot.img" image. So far so good. I have gone through official
GRUB2 manual, which is getting old, as many details are only explained on a MBR partition scheme.
I will go checking if GRUB2 is correctly set on the drive MBR. I expect it to be so, because I expect Boot-Repair did his job
correctly. But I need to know what I am expected to find there. I guess I shall look for a copy of GRUB2's "core.img" image 
file.

Once I will have checked the GRUB2 setting, I shall turn to why my UEFI/BIOS is not properly starting this properly installed
GRUB2.
I have read in some places that some BIOS GPT combinations can just be failing anyhow you try. 
I also would like to share this nice source of informations, which comments on this claim ( [http://www.rodsbooks.com/gdisk/bios.html](http://www.rodsbooks.com/gdisk/bios.html) ),
and addresses many of the questions I had in my initial post:
[http://www.rodsbooks.com/gdisk/booting.html](http://www.rodsbooks.com/gdisk/booting.html) .


> **oldfred said:**
> 
You do have a lot of kernels. Time to houseclean once you get it working.
Yes I know. Got this linux for along time. I agree I should have a cleanup.
I also like to keep a few older kernels just in case something go wrong with the newer
ones.

---

### Post by lb.rudewolf on 2016-01-14
I would like to share a temporary solution that deals the most urgent issues so far:
consistently being able to boot my former linux system.

[B]In short:
[/B]I bought a 5€ usb pendrive that I transformed into a bootable "SuperGrub2disk" 
rescue device. Booting on it I am offered an extensive set of choices to easily
have grub (from the pendrive) to load my OS (on my hardrive).

As a note, it requires me to start in EFI mode to get to this GPT USB drive,
and from there I can get back to my Ubuntu system. I still have to see if
my system can start in BIOS(CSM) mode and load a GRUB2 from a GPT drive
(I am experenting on this.)


General guidelines:
1/ Look for informations on superGrub2Disk [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/) .
2/ At this link are instructions for making a bootable drive from Windows. 
The following will address the case of making one from a Linux environment.
3/ Look at [https://wiki.archlinux.org/index.php/USB_flash_installation_media#In_GNU.2FLinux](https://wiki.archlinux.org/index.php/USB_flash_installation_media#In_GNU.2FLinux)
4/ download superGrub2Disk latest iso: [http://www.supergrubdisk.org/category/download/supergrub2diskdownload/super-grub2-disk-stable/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/super-grub2-disk-stable/) or
wget [https://forja.cenatic.es/frs/download.php/file/1844/super_grub2_disk_hybrid_2.02s3.iso](https://forja.cenatic.es/frs/download.php/file/1844/super_grub2_disk_hybrid_2.02s3.iso)
5/ be in awe of dd (do not miss this step, you are warned) and adapt
dd bs=4M if=/path/to/[FONT=Verdana]super_grub2_disk[/FONT].iso of=/dev/**sdx** && syncwith sdx being the USB drive device name. (**It may wipe out your USB key**; if you wish not to, backup or adapt this step.) As a note, this image write a GPT partition
table on your USB drive.
6/ reboot, in EFI mode, on the USB stick. (It did not work in BIOS/Legacy in mycase)
7/ from the advanced (GRUB2) menu offered, easily locate your system or whatever
you want GRUB2 to chainload/load and you are done.

---

### Post by lb.rudewolf on 2016-01-15
I am keeping update on my advances.

**Experiments:**

I tried to setup a spare USB Key into GPT with GRUB2 and to boot it from 
Legacy BIOS(CSM)... to no avail.

I then tried to boot on it by chainloading a from the GRUB2 on my SuperGrub2Disk
USB Key. I ended up with a "Invalide EFI File path" error. I note that SuperGrub2Disk
needed to be loaded from UEFI mode of the laptop.

It seems to be an issue raised by some people to know if it is possible to chainload
a MBR grub from UEFI Grub:
[https://www.debian-fr.org/comment-chainloader-vers-du-non-efi-t48000.html](https://www.debian-fr.org/comment-chainloader-vers-du-non-efi-t48000.html) .

My next experiment would be to load a Grub2 on a MBR USB Key from BIOS
modeon the laptop, and from there to manualy try to chainload a GPT BIOS 
Grub2 on another USB Key. I might try if I happen to be able to get 2 unsed
pendrive at hand. (I need one in GPT UEFI for booting my laptop at the moment.)
[B]
Documentation:
[/B]The laptop I am using is of this kind:
[http://www.thinkwiki.org/wiki/Category:X220_Tablet](http://www.thinkwiki.org/wiki/Category:X220_Tablet)
and the UEFI provided is by Intel, and at a version from 2013.
From the above link, I can read in the notes
> 
[LIST]
[*]On booting:
[LIST]
[*]The X220 cannot/will not boot GPT disks using Legacy BIOS, you must setup UEFI.
[*]The X220 will not boot /efi/*/*.efi unless "signed"(?) into BIOS, you have to copy it to /efi/boot/bootx64.efi.
[*]Disabling the BIOS setting "USB UEFI BIOS Support" disables *all* USB booting, ie, both UEFI and legacy BIOS.
[/LIST]
[/LIST]


According to this I should conclude:
**My main issue "booting in BIOS mode a GRUB2 on a GPT drive on my X220T laptop" is allegedly _not possible._**[CENTER][COLOR=#000000] :frown:
[/COLOR][/CENTER]
[COLOR=#000000]
So my next step will be to setup a UEFI booting on my old Ubuntu system. I have
met some online sources about this procedure.

Unless anyone has informations about the inability of X220 to boot GPTdisks in BIOS
mode, I guess this shall close this subject. [/COLOR]

---

