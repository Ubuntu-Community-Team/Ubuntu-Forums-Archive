---
title: "Need help Dual-Booting ubuntu Desktop 15.04 with Windows 8.1 on a separate HDD"
date: 2015-06-11
forum: General Help
---

### Post by joshua31 on 2015-06-11
So I have a desktop, an hp 500-165 or something to that effect. It has 8 GB 1600 RAM, a 2 TB HDD, and a 80 GB HDD that was salvaged from an old hp compaq 5750. I want to be able to dual boot between the disks, keeping windows 8.1 on the 2 TB HDD where it is now, and making the Ubuntu Desktop on the 80 GB HDD. I read that the process is a little bit different between booting on the same disk and on separate disks. If someone could direct me where to go, or to just tell me what to do to boot the way I just described, I would be appreciative.

---

### Post by oldfred on 2015-06-11
If new system, it is UEFI with CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

Did you install Windows in UEFI boot mode? If so you best install Ubuntu in UEFI boot mode.
And UEFI requires gpt partitioning, your old drive probably is MBR(msdos)

And second drive installs in UEFI mode will default to use ESP - efi system partition  on sda, even if you follow the directions and say to install to sdb. (it overwrote my other Ubuntu boot on sda). It will not overwrite a Windows efi boot as each has a separate folder in efi partition.

I would partition in advance and include an efi partition at beginning of drive. Or disconnect Windows drive to install to Ubuntu drive. Then use Something Else as the install option. Just be sure to choose sdb and partitions you created.

Whether BIOS or UEFI Something Else is the same. It is only how you boot installer UEFI or BIOS that determines if you are installing in UEFI or BIOS mode. UEFI gives two boot options for flash drive live installer.

      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
      
 But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

I use gparted to partition drives, for gpt you must select that first. 
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

---

### Post by joshua31 on 2015-06-11
I apologize, I am still getting familiar with the vocab and I am still not too familiar with the difference between efi and uefi, except that uefi is more gui oriented and i believe able to more easily navigated, specifically by a mouse. I am just beginning to find my way around ubuntu, and I have installed it on several computers, so I am a little familiar with the DEFAULT installation process. When installing windows 8.1 (running an AMD-A8 6500 APU if that helps) I am not confident in which mode i installed it in, whether bios or uefi. I am also not familiar with the meaning of gpt. If you could explain these to me, I would be grateful.

---

### Post by oldfred on 2015-06-11
Post this from Ubuntu live installer, if you have an efi partition and gpt(GUID) partitioning then Windows must be installed in UEFI mode. Even with Windows how you boot installer is then how it installs.

sudo parted -l

 [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

I thought I had added the acronyms to my link below, but now it is there at the very bottom.

---

### Post by joshua31 on 2015-06-11
Okay cool. I do not have time to look at the links right now (this is for a very near future project), but I will be keeping them very close. Thanks a bunch for the help, and I will let you know if I have any issues.

---

