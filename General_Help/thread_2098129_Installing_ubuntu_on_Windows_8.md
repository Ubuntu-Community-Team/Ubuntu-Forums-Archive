---
title: "Installing ubuntu on Windows 8"
date: 2012-12-25
forum: General Help
---

### Post by QsoftStudios on 2012-12-25
I just got a new laptop for X-mas and I'm having a bit of an issue. The laptop came with Windows 8 pre installed and I hate it. I want to install ubuntu 12.10 instead but I have noticed there is some weird partitions on the hard drive. There is the windows 8 partition, a UEFI partition a recovery image and a acer one button reset partition. Is it safe to wipe all of these and just install ubuntu on 1 partition? When I saw the UEFI partition I was not sure if it was safe to get rid of that because it has to do with the BIOS. 

HELP!

---

### Post by hunterkasy on 2012-12-25
EFI System partition
From Wikipedia, the free encyclopedia
Jump to: navigation, search

The EFI System partition (ESP) is a partition on a data storage device that is used by machines that adhere to the Extensible Firmware Interface. It contains the boot loader programs for all operating systems installed (in other partitions) on the device, device driver files (used by the firmware at boot time) for other devices, and system utility programs that are intended to be run before an operating system is booted.[1]

The EFI System partition is formatted using the FAT12, FAT16 or FAT32 file system. The globally unique identifier for the EFI System partition in the GUID Partition Table scheme is C12A7328-F81F-11D2-BA4B-00A0C93EC93B. Its ID in the MBR partition table scheme is 0xEF. Whether a disk contains an EFI System partition is unrelated to the partition table scheme (GPT or MBR) that it uses.

Usage
Windows

Microsoft recommends that when partitioning a disk, the EFI System partition be the first partition on the disk.[2] This is not a requirement of the EFI specification itself. On Windows XP 64-Bit Edition and later, access to the EFI System Partition is obtained by running the mountvol /s command.
Apple–Intel

On Apple–Intel architecture Macintosh computers, the EFI partition is initially blank and not used for booting.[3] However, the EFI partition is used as a staging area for firmware updates;[4] specifically, it places a firmware flash utility (EFI binary) and data file (FD – "Firmware Device"[5]) in the directory EFI/APPLE/FIRMWARE which is then run when rebooting the system in "flash firmware" mode.[6]

If deleted, the system will still boot, and the boot manager will still allow users to choose whether to start a Boot Camp partition or the default Mac OS X, but firmware updates will fail.

---

### Post by QsoftStudios on 2012-12-25
> **hunterkasy said:**
> EFI System partition
From Wikipedia, the free encyclopedia
Jump to: navigation, search

The EFI System partition (ESP) is a partition on a data storage device that is used by machines that adhere to the Extensible Firmware Interface. It contains the boot loader programs for all operating systems installed (in other partitions) on the device, device driver files (used by the firmware at boot time) for other devices, and system utility programs that are intended to be run before an operating system is booted.[1]

The EFI System partition is formatted using the FAT12, FAT16 or FAT32 file system. The globally unique identifier for the EFI System partition in the GUID Partition Table scheme is C12A7328-F81F-11D2-BA4B-00A0C93EC93B. Its ID in the MBR partition table scheme is 0xEF. Whether a disk contains an EFI System partition is unrelated to the partition table scheme (GPT or MBR) that it uses.

Usage
Windows

Microsoft recommends that when partitioning a disk, the EFI System partition be the first partition on the disk.[2] This is not a requirement of the EFI specification itself. On Windows XP 64-Bit Edition and later, access to the EFI System Partition is obtained by running the mountvol /s command.
Apple–Intel

On Apple–Intel architecture Macintosh computers, the EFI partition is initially blank and not used for booting.[3] However, the EFI partition is used as a staging area for firmware updates;[4] specifically, it places a firmware flash utility (EFI binary) and data file (FD – "Firmware Device"[5]) in the directory EFI/APPLE/FIRMWARE which is then run when rebooting the system in "flash firmware" mode.[6]

If deleted, the system will still boot, and the boot manager will still allow users to choose whether to start a Boot Camp partition or the default Mac OS X, but firmware updates will fail.


I don't really get a clear answer from that. Im a bit new to the newer hardware. So im guessing what you are saying is that it is safe?

---

### Post by oldfred on 2012-12-26
Some are having issues getting back into UEFI/BIOS. If you do not turn quick boot off then the only way to get to UEFI is thru Windows. And if you delete Windows.....

Windows partitions:
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

    
       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
Most have to turn secure boot off but still boot in UEFI mode not BIOS/legacy mode from flash drive installer.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

    
What laptop?

some that have worked.
       Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)

---

### Post by QsoftStudios on 2012-12-26
> **oldfred said:**
> Some are having issues getting back into UEFI/BIOS. If you do not turn quick boot off then the only way to get to UEFI is thru Windows. And if you delete Windows.....

Windows partitions:
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

    
       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
Most have to turn secure boot off but still boot in UEFI mode not BIOS/legacy mode from flash drive installer.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

    
What laptop?

some that have worked.
       Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)


Thanks a'lot but I am not trying to duel boot. I was wondering if it would be safe to just click the install Ubuntu button and wipe everything and just have the ubuntu partition plus the swap partition it creates.

---

### Post by hunterkasy on 2012-12-26
this is for linux mint but it should be for all distros

[http://community.linuxmint.com/tutorial/view/858](http://community.linuxmint.com/tutorial/view/858)

How to install Linux on UEFI systems where GRUB fail to install?

Hi everyone,


I&#8217;m writing this because a lot of people out there are facing some issues in installing Linux on a machine that have an EFI capable bios.


A lot are complaining that GRUB is not installing properly, leaving a computer in an unusable state. Usually they get an error message at the startup: &#8220;no operating system found&#8221; or in dual booting only windows starts up.


I&#8217;m sure this is a temporary situation, and Linux Mint will find a way to install in EFI based bios and GPT formatted HDDs easily.


In a short and simple QA I will try to explain how to fix this:


Question: Why GRUB is not installing properly in my machine?
Answer: New machines have EFI capable bios. This means that by default MS Windows is installed in UEFI mode and this requires a GPT formatted Hard Disk. At the present GRUB cannot install itself in GPT partition table without a huge effort and special skills.

Question: How to make GRUB work in my machine?
Answer: The easiest way is to convert your HDD from GPT partition table to MBR partition table (or MSDOS in Linux) and after that install your Linux Mint.

Question: How can I convert my HDD from GPT to MBR partition table?
Answer: You can use a distro of your choice in live mode. In live mode, find the program GPARTED. Wait until it recognizes all your drives and select your HDD. Right click over it, and choose the option to create a new partition table. Choose MSDOS from the list. Hit ok than apply/commit all changes. ATTENTION this will erase all your data and MS Windows (or any other OS) will disappear. Your HDD is now converted in MSDOS or MBR. You can now boot your preferred distro, create your partition scheme and install Linux.

Question: Do I need to make any changes to my bios settings?
Answer: If you have a capable UEFI and LEGACY bios, put the bios in Legacy boot only or Both enabled with Legacy boot first.

Question: Can I dual boot Win7 and Linux on a UEFI capable bios?

Answer: Yes you can. If your HDD is formatted in MBR partition table (or msdos) than you can install first windows 7 and than the distro of your choice. BUT, careful, if you install windows from a DVD media it will convert your HDD in GPT partition table and dual boot will be almost impossible... (or will give you a lot of headache) to avoid this, dump the win7 iso to an usb using Windows 7 USB/DVD Download Tool. Installing from USB will not change the hdd in GPT partition table.

---

### Post by QsoftStudios on 2012-12-26
> **hunterkasy said:**
> this is for linux mint but it should be for all distros

[http://community.linuxmint.com/tutorial/view/858](http://community.linuxmint.com/tutorial/view/858)

How to install Linux on UEFI systems where GRUB fail to install?

Hi everyone,


I’m writing this because a lot of people out there are facing some issues in installing Linux on a machine that have an EFI capable bios.


A lot are complaining that GRUB is not installing properly, leaving a computer in an unusable state. Usually they get an error message at the startup: “no operating system found” or in dual booting only windows starts up.


I’m sure this is a temporary situation, and Linux Mint will find a way to install in EFI based bios and GPT formatted HDDs easily.


In a short and simple QA I will try to explain how to fix this:


Question: Why GRUB is not installing properly in my machine?
Answer: New machines have EFI capable bios. This means that by default MS Windows is installed in UEFI mode and this requires a GPT formatted Hard Disk. At the present GRUB cannot install itself in GPT partition table without a huge effort and special skills.

Question: How to make GRUB work in my machine?
Answer: The easiest way is to convert your HDD from GPT partition table to MBR partition table (or MSDOS in Linux) and after that install your Linux Mint.

Question: How can I convert my HDD from GPT to MBR partition table?
Answer: You can use a distro of your choice in live mode. In live mode, find the program GPARTED. Wait until it recognizes all your drives and select your HDD. Right click over it, and choose the option to create a new partition table. Choose MSDOS from the list. Hit ok than apply/commit all changes. ATTENTION this will erase all your data and MS Windows (or any other OS) will disappear. Your HDD is now converted in MSDOS or MBR. You can now boot your preferred distro, create your partition scheme and install Linux.

Question: Do I need to make any changes to my bios settings?
Answer: If you have a capable UEFI and LEGACY bios, put the bios in Legacy boot only or Both enabled with Legacy boot first.

Question: Can I dual boot Win7 and Linux on a UEFI capable bios?

Answer: Yes you can. If your HDD is formatted in MBR partition table (or msdos) than you can install first windows 7 and than the distro of your choice. BUT, careful, if you install windows from a DVD media it will convert your HDD in GPT partition table and dual boot will be almost impossible... (or will give you a lot of headache) to avoid this, dump the win7 iso to an usb using Windows 7 USB/DVD Download Tool. Installing from USB will not change the hdd in GPT partition table.


Thanks a'lot for the input but I am really just asking a yes or no question. When I install ubuntu can I select use entire drive and use *Delete windows 8 and install Ubuntu 12.10* ?

---

### Post by hunterkasy on 2012-12-26
> **QsoftStudios said:**
> Thanks a'lot for the input but I am really just asking a yes or no question. When I install ubuntu can I select use entire drive and use *Delete windows 8 and install Ubuntu 12.10* ?

I say go for it, may have to make a change in the bios but if you delete the partition and create a new one"s" with linux I am guessing it should work, if not you will be on here asking for help either way I say go for it

---

### Post by QsoftStudios on 2012-12-26
> **hunterkasy said:**
> I say go for it, may have to make a change in the bios but if you delete the partition and create a new one"s" with linux I am guessing it should work, if not you will be on here asking for help either way I say go for it

*Takes deep breath* Ok thanks I just wanted to make sure cuse its a BRAND new laptop and I really wouldn't want to brick it.

---

### Post by QsoftStudios on 2012-12-26
> **hunterkasy said:**
> I say go for it, may have to make a change in the bios but if you delete the partition and create a new one"s" with linux I am guessing it should work, if not you will be on here asking for help either way I say go for it


:D:D:D YES! the default install has worked. Ubuntu recognized the UEFI bios and made its own 90mb EFI partition. 

I can confirm it works on an Acer Aspire V5-471 laptop computer. I will now mark this as solved, thanks guys!

---

### Post by oldfred on 2012-12-26
Glad you got it working.

Yes we have seen many installs of Ubuntu to UEFI systems, some older that had Windows 7 and no secure boot and some newer with Windows 8 and secure boot option.But you need 64 bit version and grub2 version 2.00.

Also there is no real issue using gpt partitions. I have gpt partitions on two drives and a flash drive. The only thing was older versions you had to create a bios_grub 1MB unformatted partition to get grub to install correctly. New versions install correctly.

---

