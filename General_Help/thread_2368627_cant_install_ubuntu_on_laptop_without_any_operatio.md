---
title: "cant install ubuntu on laptop without any operation system"
date: 2017-08-13
forum: General Help
---

### Post by milosz4206 on 2017-08-13
as the title says i cant install ubuntu on my laptop, when im on part with the partitions etc im clicking that delete all programs files etc and install ubuntu but when im selecting it 10 sec later error is popping out and its says that ,,cant create ext4 file on partition'' something like that then the same message is popping out again but with ext3 etc.My laptop shutted down 2 weeks ago and i cannot enter windows so i tried to repair my computer option with live usb but nothing helped so i entered cmd and just cleaned my disk,anyway when im installing ubuntu and the error is popping idk if my hard drive is damaged or something when i enter cmd its showing in list disk and its showing that about 930gb is free.here is gparted screen,also when im in the boot menu where i select what to boot it says that there is 2 usb sticks but i plugged only one, one is sata hdd usb and second one is efi usb (im on it). [http://iv.pl/images/22644901519617187058.png](http://iv.pl/images/22644901519617187058.png)

---

### Post by johndough2 on 2017-08-13
Hi

Perhaps the problem is in the BIOS, in that Secure Boot is enabled.  This is an area to investigate.

So Windows failed and you want to use your laptop?  There is a no mention of what Windows Operating system it was.

You could make a W10 recovery disk, if you have access to another windows machine, 
[https://www.microsoft.com/en-us/software-download/windows10](https://www.microsoft.com/en-us/software-download/windows10)

Download and create a DVD or USB stick.

A reason why the partition won't format, maybe, is because it was not shut down cleanly and Gparted cannot access the area to write any changes.

Search for " use 'ntfsfix', which was part of the old ntfsprogs package and is now located in the ntfs-3g package to clean an ntfs partition."
 ntfs-3g ;  ntfs-config ;  ntfsprogs ;   testdisk ;

If you give a little more detail on the old OS and the exact error message it could be helpful.

If in doubt please ask.

---

### Post by milosz4206 on 2017-08-13
I had win 10 updated from win 8.1 but something messed up and i used system recovery but it didnt help so i made win 8.1 usb stick and tried repair option but it didnt help too so i enter cmd from windowa usb stick and cleaned disk from diskpart now i wanted to install ubuntu on this laptop but the error is popping out saying that he cant create partitions. I cant install windows too. Computer is comletely clear and have no operating systen.(even on ubuntu installation its saying that there is no operating sysyem on the computer) i hit u up with more screens when i back home.

---

### Post by Autodave on 2017-08-13
Using gparted, I would remove all partitions and try it. If that doesn't work, again using gparted, I would make one partition of the whole drive and format it to ntfs and try again.

---

### Post by ajgreeny on 2017-08-13
> I enter cmd from windows usb stick and cleaned disk from diskpartI do not use Windows and know nothing about diskpart which you mention in your original post, but if that means that you made a partition for Linux using Windows I think it could be a dynamic partition, hence the "unknown" in the gparted shot, as Linux can not see, ubderstand, nor use dynamic partitions.

If you do not want Windows any more you may need to use gparted from the live Ubuntu system and create a new partition table from the Device menu.  Create a GPT table, not the default msdos, and then try again to install using the whole disk.  It will automatically create partitions for EFI, root and if installing 16.04, which I recommend rather than 17.04, you will also get a swap partition, 17.04 will use a swap file instead so no swap partition will be made.

If you do want to keep Windows in any form I will leave it to others to help as I am totally out of my knowledge zone dealing with that OS.

---

### Post by milosz4206 on 2017-08-13
> **ajgreeny said:**
> I do not use Windows and know nothing about diskpart which you mention in your original post, but if that means that you made a partition for Linux using Windows I think it could be a dynamic partition, hence the "unknown" in the gparted shot, as Linux can not see, ubderstand, nor use dynamic partitions.

If you do not want Windows any more you may need to use gparted from the live Ubuntu system and create a new partition table from the Device menu.  Create a GPT table, not the default msdos, and then try again to install using the whole disk.  It will automatically create partitions for EFI, root and if installing 16.04, which I recommend rather than 17.04, you will also get a swap partition, 17.04 will use a swap file instead so no swap partition will be made.

If you do want to keep Windows in any form I will leave it to others to help as I am totally out of my knowledge zone dealing with that OS.

nah i used diskpart to clear my disk and delete everything.Would be great if u help me with step by step cuz i dont know ubuntu that well and i can mess something up

---

### Post by milosz4206 on 2017-08-13
> **Autodave said:**
> Using gparted, I would remove all partitions and try it. If that doesn't work, again using gparted, I would make one partition of the whole drive and format it to ntfs and try again.

so just delete these 3 partitions that are in screen ?

---

### Post by oldfred on 2017-08-13
You are showing an ESP partition sda1, a corrupted or locked sda2 and swap with locked (mounted icon).

Is/was sda2 NTFS or ext4? If Windows and you have Windows fast start up on which is really hibernation, Linux tools will not touch it as it does not want to damage your Windows NTFS partition.
And you have to swap off to remove lock icon on sda3.

Is screen shot from gparted on live installer?

---

### Post by milosz4206 on 2017-08-13
> **oldfred said:**
> You are showing an ESP partition sda1, a corrupted or locked sda2 and swap with locked (mounted icon).

Is/was sda2 NTFS or ext4? If Windows and you have Windows fast start up on which is really hibernation, Linux tools will not touch it as it does not want to damage your Windows NTFS partition.
And you have to swap off to remove lock icon on sda3.

Is screen shot from gparted on live installer?

sda 2 was my C partition and it was NTFS i think when it was in windows,there is no windows boot manager in boot options so there is no way windows is still on the laptop,im running ubuntu from pendrive with try ubuntu without installing option

---

### Post by milosz4206 on 2017-08-13
btw now in gparted its showing me that : [http://iv.pl/images/89617831956822187834.png](http://iv.pl/images/89617831956822187834.png) now they changed their places and there is no partition named EFI

---

### Post by oldfred on 2017-08-13
You converted it from gpt to MBR(msdos).
Gpt does not have an extended partition.

The ESP is required for UEFI boot by Widnows, and really should be used by Ubuntu for UEFI boot.
Windows only boots in BIOS mode from MBR partitioning.

You can use a Windows repair flash drive add Windows boot files to an otherwise ok, NTFS partition with boot flag in BIOS/MBR mode. Boot flag has to be on ESP with gpt partitioning. 
And Windows repair flash drive should work around other issues like hibernation or needing chkdks, that you cannot do from Linux.

Do you want UEFI or BIOS boot? Partitioning gpt or MBR has to match.

---

### Post by milosz4206 on 2017-08-14
> **oldfred said:**
> You converted it from gpt to MBR(msdos).
Gpt does not have an extended partition.

The ESP is required for UEFI boot by Widnows, and really should be used by Ubuntu for UEFI boot.
Windows only boots in BIOS mode from MBR partitioning.

You can use a Windows repair flash drive add Windows boot files to an otherwise ok, NTFS partition with boot flag in BIOS/MBR mode. Boot flag has to be on ESP with gpt partitioning. 
And Windows repair flash drive should work around other issues like hibernation or needing chkdks, that you cannot do from Linux.

Do you want UEFI or BIOS boot? Partitioning gpt or MBR has to match.

i dont understand half of this, i just want windows again,but as i said i cant even install windows and ubuntu, thats why i am on live usb right now

---

### Post by johndough2 on 2017-08-14
Hi

I think you should wipe everything to have a single blank HDD.

Then as said above create a GPT partition, just a SINGLE partition and format it.

If you can achieve that, whether it is NTFS or ext4 does not matter, because at that point you have cleared any and all problems with the old NTFS Windows partition.

From this point the install should go cleanly, and if the installer wants to automatically partition I would accept that and continue.

So clear the whole disk and use GPT.

If in doubt please ask.

---

### Post by johndough2 on 2017-08-14
Hi

"i dont understand half of this, i just want windows again"

To install windows I would find a Windows machine, down the Microsoft CREATOR tool and CREATE an install USB.  It is automatic.  Needs 4 Gb of space and about an hour.

Then install onto your machine. 

[https://www.tenforums.com/](https://www.tenforums.com/)   there are thousands of tutorials and help pages.  
[https://www.tenforums.com/tutorials/1950-clean-install-windows-10-a.html](https://www.tenforums.com/tutorials/1950-clean-install-windows-10-a.html)

If in doubt please ask.

---

### Post by johndough2 on 2017-08-14
Hi

Using Linux only.... Windows 10 iso is available from here...

Download windows 10 in opensuse

[http://www.technicalnotes.org/direct-link-download-windows-10-iso-without-media-creation-tool/](http://www.technicalnotes.org/direct-link-download-windows-10-iso-without-media-creation-tool/)

    Download Windows 10 ISO 32-bit   [https://www.microsoft.com/en-us/software-download/windows10ISO/](https://www.microsoft.com/en-us/software-download/windows10ISO/)
    Download Windows 10 ISO 64-bit   [https://www.microsoft.com/en-us/software-download/windows10ISO/](https://www.microsoft.com/en-us/software-download/windows10ISO/)

but you will need somewhere to save the 4 Gb iso file prior to creating a USB medium, and a suitable utility.

---

### Post by oldfred on 2017-08-14
If you want UEFI only, but have to set system to boot flash drive in UEFI mode and have system set to boot all installs in UEFI mode.

 UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
[https://help.ubuntu.com/community/mkusb/v7#Making_a_USB_drive_to_install_Windows](https://help.ubuntu.com/community/mkusb/v7#Making_a_USB_drive_to_install_Windows)

---

### Post by Autodave on 2017-08-14
In the BIOS, make sure that *fast boot *is turned off.  Then in *gaprted, *remove all partitions. Then, create one partition using the entire disc.

---

