---
title: "Creating an Install Hard Drive"
date: 2015-06-11
forum: General Help
---

### Post by cranerja on 2015-06-11
How would one go about creating a hard drive with partitions containing different install ISOs from various operating systems?

---

### Post by Bashing-om on 2015-06-11
cranerja; 
Hey ; it is Prior Prudent Planning Preventing Pi** Poor Performance:

Mine:
```

sysop@1404mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   102402438    51200195+  83  Linux
/dev/sdc2   *   102404096   204804095    51200000   83  Linux
/dev/sdc3       204806144   266246143    30720000   83  Linux
sysop@1404mini:~$

sysop@1404mini:~$ sudo blkid
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="1404std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdc2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdc3: LABEL="ubie1504" UUID="2ec4733f-db40-4db0-aef8-5c54e54085ab" TYPE="ext4" 
sysop@1404mini:~$ 

```

The trick is to take care of the boot loader !

[INDENT][INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

### Post by yancek on 2015-06-11
> How would one go about creating a hard drive with partitions containing different install ISOs from various operating systems? 		

If you want the iso files on a hard drive partition to use to boot and install on other partitions you can do that from any partition including the /.  The trick is getting correct boot entries in the menu of your current system to boot them so you can install.  Grub in Ubuntu should be no problem, lots of links and info available on that if that's what you are asking?

---

### Post by cranerja on 2015-06-11
I want to know the best way to get isos onto the partitions. I have tried with dd but I really don't know how to install grub manually either.

---

### Post by grahammechanical on 2015-06-11
I am assuming that you want to do more than just copy some ISO images onto a hard disk. I am assuming that you want to install different operating systems.

It all depends on what OS you already have. If it is a Microsoft OS and you want to keep it, then you must use a Windows tool to defrag the hard disk more than once, making sure that Windows loads each time

Then you use a Windows tool to resize and if necessary remove Windows partitions to create unallocated space that can be used to create Linux partitions. Each Linux operating system would need 20 GB to 30 GB partitions. You could get away with a little as 15 GB. To create these partition we use Gparted from a Ubuntu live session.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

But again it all depends on whether the motherboard has a BIOS boot system or UEFI boot system and whether the Microsoft OS is Windows 8. Things can get complicated. And you say nothing about the hardware that you are using.

Regards.

---

### Post by cranerja on 2015-06-11
I'm trying to make an external drive that when booted, displays a grub menu which as entries for multiple operating systems. This would be used for installing on multiple computers. I'm trying to figure out how to "burn" the iso but to a partition rather than a disk.

---

### Post by Bashing-om on 2015-06-11
cranerja; Well;

There is no one answer fits any/all use cases.
However, generally - what I do - is Have a blank hard drive, and on this canvass I partition 3 partitions for that 1st system install;
2 partitions as type primary: 20 Gigs for '/' , 30 Gigs for /home.
The majority of the remaining space as an 'extended' partition . In the extended partition I make up something for swap partition ( depending on how much ram is onboard and how intensive I will drive the system). 
Within this 'extended' partition I would make up partitions for other systems I would in the future install. Very small and tight if they are to be but 'test' installs. All installs will share the /swap partition as common to all .

Once the partitions are set up, just point the installer to the proper designation, select 'change in the installer and confirm there what the selected partition is going to be used for and how large  and if it is to be formatted at that time.
Answer the wizard questions as to locations and keyboard, username and password, ========> confirm where grub is going to be installed.

Grub will take care of adding each operating system to the boot menu . Now, how you maintain the boot is an art in and of it's self. There are many many solutions to maintain a stable boot condition to boot any installed system. You will learn what works best for you.

All there is to it
[INDENT][INDENT]easy peasy
[/INDENT][/INDENT]

---

### Post by oldfred on 2015-06-11
UEFI or BIOS? or Both.
BIOS is relatively easy. And I think if I had not done BIOS versions, I would not have figured out UEFI version. 
I have ISO on each of my two installed hard drives for installing into the other drive and on flash drives either BIOS or UEFI.

 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

Also this:

  How to Create a EFI/UEFI GRUB2 Multiboot USB drive to boot ISO images
[http://ubuntuforums.org/showthread.php?t=2276498](http://ubuntuforums.org/showthread.php?t=2276498)
Bootable UEFI USB Key
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[http://ubuntuforums.org/showthread.php?t=2015019](http://ubuntuforums.org/showthread.php?t=2015019)

---

### Post by yancek on 2015-06-12
The method for using a hard drive to store multiple iso file which you can then boot to install on another computer is the same as making a multi-boot flash drive.  You would need to first install Grub to the drive and then simply copy the iso files to the partition or another partition on the drive.  You would need to install Grub to the hard drive and manually create entries in the grub.cfg file.   The links posted by oldfred, particularly the first one should give you some examples.  You would need to set this drive to first boot priority on the new computer and generally when doing that the entry in Grub will need to show it as the first drive.  Don't know about UEFI.

---

