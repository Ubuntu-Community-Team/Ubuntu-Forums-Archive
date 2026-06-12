---
title: "Reinstall MBR"
date: 2016-02-01
forum: General Help
---

### Post by eliott on 2016-02-01
Hello,
[FONT=arial]
I set up a dual boot on my Dell xps 13 but my network does not work and ubuntu won't shutdown. So I want unstall ubuntu 14 and install the 15. 

I boot on a USB key to install and execute boot repair to reinstall the MBR but I get the message that informs all of partition need to be unmount and after I have this message:

[/FONT][FONT=arial]/var/log/boot-sav/log/2016-02-[/FONT][FONT=arial]01__13h52boot-repair41/sda/[/FONT][FONT=arial]current_mbr.img does not exist. MBR could not be restored.[/FONT]
[FONT=arial]
the report of boot repairer is here : [http://paste2.org/vZaIBw4y](http://paste2.org/vZaIBw4y)

what should I do ?
[/FONT]
[FONT=arial]thank you beforehand[/FONT]

---

### Post by ajgreeny on 2016-02-01
You do not need to uninstall Ubuntu 14.xx to install Ubuntu 15.xx, unless, of course, you will not be reinstalling for a period in which you need to use Windows

Install as you would normally but this time choose to use "Something Else" at the partitioning part.

Now highlight in the large ext4 partition that it will show, click the Change button and choose to use it as either a primary or logical partition (as it was before), also choose to use it as ext4 and mountpoint /, ie root. Click to select the checkbox for "Format".
Now you can click in the swap partition and choose to use it as swap again.  Click to install.

Grub will now be installed to the MBR and overwrite the version you have at the moment.

---

### Post by grahammechanical on 2016-02-01
Boot Repair is not seeing your storage media. It is only seeing the USB memory stick which it is calling sda. You have NVMe and it seems that boot repair is not very good at dealing with NVMe

> /dev/nvme0n1p1: LABEL="ESP" UUID="D0CB-FEC9" TYPE="vfat"

/dev/nvme0n1p3: LABEL="OS" UUID="7EB03650B0360EE1" TYPE="ntfs"

/dev/nvme0n1p4: LABEL="WINRETOOLS" UUID="FC54C23454C1F186" TYPE="ntfs"

/dev/nvme0n1p5: LABEL="Image" UUID="8CE0C242E0C2326E" TYPE="ntfs"

/dev/nvme0n1p6: UUID="99fd3738-86da-4448-8544-47e88d1bf348" TYPE="ext4"

/dev/nvme0n1p7: UUID="7e936735-7fe3-44bc-9397-ce4dd5d10075" TYPE="swap"



[https://en.wikipedia.org/wiki/NVM_Express](https://en.wikipedia.org/wiki/NVM_Express)

But we do not reinstall the MBR because the MBR is a special part of the hard disk. If we are dual booting with Windows & Linux and we want to remove Linux we need to re-install the Windows boot loader before removing the Linux OS. Is that what you want to do?

You have GPT partitioning. So you do not need to worry about logical partitions. Actually nvme0n1p6 is the partition to install Ubuntu in using the Something Else option. I cannot tell you what label the Ubuntu installer will show when you get to the screen showing the partition layout but Ext4 is a good clue.

Keep away from the ntfs partitions. They are for Windows. The partition that is formatted vfat is the ESP partition. It is where Windows keeps its efi boot files. Do not touch that. Load the Ubuntu live session in efi mode and Ubuntu will install in efi mode and the Ubuntu installer can make use of that vfat - efi boot partition to put the Ubuntu efi boot files in.

> Disk /dev/nvme0n1: 256GB

 	Sector size (logical/physical): 512B/512B

 	Partition Table: gpt

  
	Number  Start   End    Size    File system     Name                          Flags

 	1      1049kB  525MB  524MB   fat32           EFI system partition          boot

 	2      525MB   660MB  134MB                   Microsoft reserved partition  msftres

 	3      660MB   162GB  161GB   ntfs            Basic data partition          msftdata

 	6      162GB   225GB  63.1GB  ext4

 	7      225GB   241GB  16.4GB  linux-swap(v1)

 	4      241GB   242GB  915MB   ntfs                                          hidden, diag

 	5      242GB   256GB  13.8GB  ntfs                                          hidden, diag



I cannot help more than this.

Regards.

---

### Post by oldfred on 2016-02-01
With UEFI you do not use the protective MBR that gpt partitioning has. That is just to have one entry saying drive is gpt partitioned, so old MBR(msdos) tools do not see drive as empty and try to partition it.

May be better to use gparted to partition, but you need a newer version than in installer.
 gparted should be at least version 0.24.0-1 to recognize NVMe devices
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

      
 ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)

Post #14 mentions this works for Dell
"nvme_load=YES" on the linux boot command.
[http://www.dell.com/support/article/us/en/04/SLN151664/en](http://www.dell.com/support/article/us/en/04/SLN151664/en)

---

