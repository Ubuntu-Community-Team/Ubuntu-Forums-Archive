---
title: "Installing Ubuntu on new computer with UEFI BIOS?"
date: 2014-12-31
forum: General Help
---

### Post by garyed on 2014-12-31
I've haven't built a new computer in quite a few years but already ordered everything & will be using a Gigabyte MB with UEFI bios. 
I plan on dual booting with Win7 on one HD & Ubuntu on a second HD. This is all from scratch so the all the drives will be unformatted & both OS's will need to be installed. I know it's easier to install Windows first on a dual boot system but I have no idea about this UEFI bios & new disk partitioning that comes with it. Does anyone have any recommendations on the sequence & preparations I should make before installing the OS's?

---

### Post by Dennis N on 2014-12-31
You can probably avoid the UEFI thing by installing both OSes in Legacy Mode since you are installing them yourself on a new system. If you want to experience UEFI, then you need to create a GPT partition table on each disk and proceed from there. As you say, Install Windows first, then Ubuntu.

Linux on UEFI: a Quick Installation Guide:

[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

---

### Post by Dennis N on 2014-12-31
When I did my first UEFI installation, I essentially followed this series of steps and it was successful. Besides studying the Rod's Books link I gave in post #2, which provides vital background information, this might be helpful. 

[http://ubuntuforums.org/showthread.php?t=1958383&p=11906060#post11906060](http://ubuntuforums.org/showthread.php?t=1958383&p=11906060#post11906060)

---

### Post by garyed on 2014-12-31
Thanks,

I didn't know if Windows 7 or Ubuntu would install on a GPT partition table either.

---

### Post by Dennis N on 2014-12-31
Just to add, If you install in Legacy mode on a UEFI system, you can still use a GPT partition table instead of the old MS-DOS (MBR) partition table. With GPT, all the partitions are primary partitions and by default there are 128 of them (should be enough for most people). I have done this on another UEFI system I have, but it does not have Windows installed on that computer. so I am assuming here that Windows can be installed that way (Legacy Mode + GPT instead of Legacy Mode +MBR) too.

You can even use GPT partitioning on a non-UEFI system - I now use GPT on my 7 year-old Dell laptop.

---

### Post by Jerry N on 2014-12-31
Since you are using two separate hard drives for your Windows and Ubuntu installations, the order of installation does not make any difference.  Just make sure that each one boots from its own drive.  If you install Windows last, you update grub in Ubuntu and it automatically finds Windows.  

Jerry

---

### Post by garyed on 2014-12-31
Another question I can't quite grasp is what type file system should I select for Linux & Windows. Do i still use EXT4 for Linux & NTFS for Windows?

---

### Post by Dennis N on 2014-12-31
> **garyed said:**
> Another question I can't quite grasp is what type file system should I select for Linux & Windows. Do i still use EXT4 for Linux & NTFS for Windows?

Yes, that's correct for the OS partitons. The EFI system partition is FAT32.

---

### Post by garyed on 2014-12-31
> **Dennis N said:**
> .........**The EFI system partition is FAT32**.

I'm not sure what that means. What is the EFI system partition? Is it totally separate from the OS partitions?

---

### Post by garyed on 2014-12-31
What I usually do before installing Ubuntu is use Gparted to partition my HD's first & then install the OS. I assume I can do the same thing with the EFI bios. I'm just not familiar with GPT or even how do I go about setting it up. Will Gparted give me that option or will Grub do it?

---

### Post by Dennis N on 2014-12-31
> **garyed said:**
> I'm not sure what that means. What is the EFI system partition? Is it totally separate from the OS partitions?

Yes it separate and required. Suggested size is 200mB and you put it first on the disk, format it FAT32, and set its flag with gparted to "boot". Each OS you install puts some boot files in that partition - both Windows and Linux.

see "Preparing your ESP" and "Using the ESP" in the "Installing Linux" section on Rod's Web Page:

[http://www.rodsbooks.com/linux-uefi/#preparing](http://www.rodsbooks.com/linux-uefi/#preparing)

---

### Post by garyed on 2014-12-31
I think I got it now. 
The EFI is already set in the BIOS.
Here's my plan:
1 - use Gparted to create the ESP partition as the first one on my first HD & make it a 200MB fat32 partition.
2 - make my NTFS & EXT4 partitions for windows & Linux.
3 -Install Windows 7 
4 - Install Ubuntu as a dual boot system  
 I assume that Gparted will give me the option to use GPT when I start to partition my drives. 

Does that sound logical?

---

### Post by Dennis N on 2015-01-03
> **garyed said:**
> I think I got it now. 
The EFI is already set in the BIOS.
Here's my plan:
1 - use Gparted to create the ESP partition as the first one on my first HD & make it a 200MB fat32 partition.
2 - make my NTFS & EXT4 partitions for windows & Linux.
3 -Install Windows 7 
4 - Install Ubuntu as a dual boot system  
 I assume that Gparted will give me the option to use GPT when I start to partition my drives. 

Does that sound logical?

Sorry for the delayed reply - yes, you have essentially it right. The EFI system partition needs to have its boot flag set. Remember to install Windows 7 and Ubuntu both in UEFI mode - otherwise, Ubuntu's grub won't be able to detect the Windows install. Gparted will indeed do gpt: use [B]Device > Create Partition Table > GPT
[/B]

---

### Post by oldfred on 2015-01-03
I have seen some that say the Windows 7 installer has to be slightly modified and only installed from a flash drive. Others have said it will install in UEFI mode from DVD. Not sure if version difference or not.

But both with Windows & Ubuntu how you boot installer is how it will install. Windows also requires another system reserved partition just before the main NTFS partition. If you let Windows partition drive it will do that automatically.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

If installing on separate drives, probably best to disconnect the other drive when installing. Each install my default to an efi partition on the other drive and better to have an efi partition on each drive. Only one efi partition per drive.

Gigabyte Motherboards seem to have an IOMMU setting that must be changed to get various things working. And Since Windows 7, you will not have secure boot. Some motherboard manufacturers are just calling that Windows boot mode, but if you have that on, it will want secure boot, but Windows 7 does not have secure boot. My Asus motherboard just called it "other OS".

      
 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....
Installers will default to gpt if you install in UEFI mode. If you install in BIOS mode, Windows has to have MBR partitions, Ubuntu will work from a gpt drive with either BIOS or UEFI, but you need a bios_grub for BIOS boot or the efi partition for UEFI boot. I actually put both on my new drives, even though using UEFI.

---

### Post by garyed on 2015-01-03
Thanks for the info oldfred,

It seems to me that if the Windows installer will do all the partitioning that it needs for EFI/GPT that I might be better letting it do it on my first drive before messing with gparted or grub. Windows is a lot more finicky than Ubuntu so I'm a little more concerned with it's intsall than Ubuntu. I'm assuming after installing windows if I mess the MBR up installing Ubuntu I'll eventually be able to get it back with grub unless I mess up the partitions. It looks like EFI & GPT are here to stay so I may as well learn them as I go to keep up with the times. I'm really building a DAW for both Windows and Linux so I'm going to be installing Ubuntu Studio 14.04. If I use gparted to do the partitioning after the windows install it should work out O.K., I hope.

---

### Post by oldfred on 2015-01-03
One of many suggestions on partitioning. How you will use system makes a difference. With new drives I find I do not need all the space so I do not fully partition, initially. And I often keep adding 25GB / partitions to test something.

 
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by garyed on 2015-01-03
Great info

From what I've been reading it seems like if you let windows installer partition the drive, the EFI partition will only be 100 MB.

---

### Post by oldfred on 2015-01-04
You actually do not use much of efi partition. The 100MB will work for single drive installs and both Windows & Ubuntu efi folders. The large size is suggested so that in future if you wanted to use rEFInd, move kernels into efi partition for direct kernel boot or some other newer way, you have the space. Most users probably will not need it, but an extra couple 100MB on new drives is not much space and adding that later is very difficult.

---

### Post by garyed on 2015-01-08
Well I put my new computer together & decided to just hook up one HD & install Win7 pro first & let Windows partition it GPT.  I figured once i get Windows running Ubuntu would be a breeze to install & dual boot. Windows is up & running fine & I still have only one HD hooked up.  The problem is with a live cd Gparted only recognizes the whole drive as being unallocated. It gives a warning that "...it does not have a fake msdos partition table.." & then it asks me if it's a GPT partition. I can view the windows files in the file manager(Thunar) but Gparted still doesn't recognize the file system. If I go back to windows it shows two partitions, one 100 MB reserved & then the other for the rest of the drive. The one thing I'm thinking that might be causing a problem is that the reserved partition which I'm assuming holds the boot info is not a FAT32 but an NTFS filesystem. Helllllllllllllll.....p

---

### Post by oldfred on 2015-01-09
That is a standard BIOS boot install with MBR partitions. And if drive was gpt, then Windows does not correctly or fully convert to MBR. It leaves the backup gpt partition table, so Linux tools see both MBR & gpt and assume you want to erase drive to fix it. You can use fixparts to remove backup gpt data if you want BIOS/MBR.

With new UEFI systems, how you boot install media is how it installs. So if you want Windows in UEFI mode you need to boot installer in UEFI mode. And Windows 7 needs some updates to flash drive installer to work in UEFI mode. (Some said it does work, so it may depend on version?)

 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

If you keep Windows in BIOS boot mode, be sure to install Ubuntu in BIOS boot mode. But with Ubuntu you still can use gpt and have both an efi partition perhaps if you want to change or try UEFI boot later, but for BIOS boot must have the bios_grub partition. If MBR neither partition is required.

---

### Post by garyed on 2015-01-09
Thanks Oldfred,
I've done plenty of dual boot installs in BIOS mode with MBR without a problem but this EFI stuff has got me stumped. 
I really wanted to use EFI & GPT for my setup not because of any features that I think I'll need, but more as a learning experience and to be ready for the future. It looks like EFI & GPT are going to become the standard so I wanted to get more familiar with them. What I realized is that my MB(Gigabyte Z97X-SLI) has a dual bios that was set for both Legacy & EFI so even though I though I was booting in EFI mode, either one could be used for the install. I tried installing Windows on a clean drive in EFI mode but then it wouldn't install because there was no GPT partitions. I assume I could use Gparted to make the GPT partitions but I'm not sure of the correct order & how many. For now I've got Windows in MBR on one drive & Ubuntu in GPT on a second drive.  I have to change the boot order in the BIOS to dual boot. Not very good but until i get this solved it allows me to run either OS. I'd love to see a Gparted screenshot of a dual boot system with Windows 7 in GPT.

---

### Post by oldfred on 2015-01-09
If a Gigabyte motherboard did you have to turn on IOMMU?

 Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

It looks like Windows only defaults to three partitions, efi, system reserved & main install. The 1MB at beginning of drive is just because first partition now starts at sector 2048.
[http://ubuntuforums.org/showthread.php?t=2251167](http://ubuntuforums.org/showthread.php?t=2251167)

Post #14 shows Windows UEFI partitions, but when you install it yourself, you do not get the Microsoft and Vendor recovery partitions.

---

### Post by garyed on 2015-01-09
I don't know what  IOMMU is so I'll have to read up on it & get back on that.

Here's a screenshot from windows disk manager:

Disk 0 should be my Ubuntu install
Disk 1 is an unformatted drive
Disk 2 Windows install

Windows says its a GPT partition in some place I can't remember and in another place it calls it an MBR partition.

---

### Post by oldfred on 2015-01-09
More IOMMU
 IOMMU for USB3 ports Gigabyte board
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)
Linux kernel enable the IOMMU – input / output memory management unit support - AMD 
[http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html](http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html)

Your third drive has to be MBR as Windows only boots in BIOS mode from MBR and you have a standard BIOS install with 100MB boot partition and Windows.

With larger 1TB drives you should think about smaller system partitions and larger data partitions.

Do not fully understand Windows screen shots but even gparted does not show MBR or gpt.
This will:
sudo parted -l

---

### Post by garyed on 2015-01-09
> $ sudo parted -l
 
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? yes                                                               
Model: ATA ST1000DM003-1ER1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Model: ATA ST1000DM003-1ER1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32                 boot
 2      538MB   983GB   983GB   ext4
 3      983GB   1000GB  17.1GB  linux-swap(v1)


Model: ATA ST1000DM003-1ER1 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size   File system  Name                          Flags
 1      17.4kB  134MB  134MB               Microsoft reserved partition  msftres



sda is the HD with the Windows partition.  If I answer "No" to the prompt it gives me then sda does not even show up using parted -l so I answered "Yes".  
sdb is Ubuntu drive & sdc is a blank HD.

Here's some gparted screen shots :

---

### Post by oldfred on 2015-01-10
Your sda or Windows drive has to be MBR. Windows standard BIOS/MBR install is the 100MB boot partition and the c:drive partition.

You third drive must have been formatted with Windows as it always adds the system reserved at the beginning of every drive.
I suggest the efi and/or bios_grub at the beginning of every drive so then you could add another install and have its boot loader on the same drive. 

Fdisk does not work with gpt drives, it is supposed to only see the protective MBR with one gpt entry, so it knows that drive is not blank. But it should work for the Windows disk.
sudo fdisk -lu

---

### Post by garyed on 2015-01-10
Well I finally got dual booting working in EFI & GPT with Windows 7.
If I had taken the advice earlier I think I wouldn't have had any problems but here's what I did.

First I set my bios to EFI mode only in boot options and periphials.
I used Gparted and a clean 1TB HD.
When I partioned the drive in Gparted I chose the GPT option. 
Partitioned in this order:
1 - 450 MB  fat32   boot flag set
2 - 350 MB NTFS
3 - 450 GB NTFS (approx) 
4 - 45 GB  ext4
5 - 450 GB ext4 (approx)
6 - 16 GB  swap
 
Then I booted with my Windows 7 pro OEM disk and when it asked me where to install windows I chose partition # 3.
Windows installed fine & once that was done I just told Ubuntu to use #4 as /, #5 as /Home & #6 as swap.

The dual boot works fine now and my bios is set to EFI and I'm using GPT partition tables.

I just added two extra HD's which was no problem.
One I formatted NTFS so Windows can use it & the other EXT4  
 
 Thanks for all the help, especially Oldfred
 Here's some screenshots, 1 from Windows & 1 from Gparted:

---

### Post by oldfred on 2015-01-10
Windows seems to want a system reserved or 128MB partition. It does not seem to be absolutely required. But some Windows software used to write DRM code or serial numbers in the area after the MBR in BIOS/MBR systems. But that space does not exist. Similarly Grub needs a bios_grub partition for core.img that in MBR is written just after MBR in BIOS/MBR systems.

Your efi partition is large enough to shrink by 128MB and create the sytem reserved partition. You may not ever need it, but better to have it.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by garyed on 2015-01-10
I already added the second partition (D) for the MSR partition after the EFI system partition but the Windows install didn't use it. I think it depends on which install version of Windows you use as to what partitions it needs. 
Are you saying I need another partition for Grub now or that I would need one if i decide to go back MBR partitioning?

---

### Post by oldfred on 2015-01-11
Formats and types are important with gpt partitioning. Your extra partition in front of your main Windows install is just another NTFS data partition.

The Windows system reserved is unformatted space and has a msftres type. Not sure if in gparted it is exactly msftres. The actual partition type with gpt is a very long GUID and different partitioning tools use different codes to simplify it. Gparted uses one set and gdisk a different set.

If you want to test install of Ubuntu or other Linux in BIOS mode on a gpt partitioned drive you must have a bios_grub partition. It is 1 or 2MB so very small and must not be formatted and can be anywhere on drive. Normally efi partition should be near beginning of drive, but Windows often makes it the second or even third partition, but first one or two are smaller repair or utility partitions.

Grub menu can only boot other installs in the same boot mode or once you start booting in UEFI you cannot from grub boot a BIOS install. But you can boot from UEFI/BIOS or perhaps one time boot key installs in BIOS or UEFI.

---

### Post by garyed on 2015-01-11
> **oldfred said:**
> Formats and types are important with gpt partitioning. Your extra partition in front of your main Windows install is just another NTFS data partition.

The Windows system reserved is unformatted space and has a msftres type. Not sure if in gparted it is exactly msftres. The actual partition type with gpt is a very long GUID and different partitioning tools use different codes to simplify it. Gparted uses one set and gdisk a different set.

If you want to test install of Ubuntu or other Linux in BIOS mode on a gpt partitioned drive you must have a bios_grub partition. It is 1 or 2MB so very small and must not be formatted and can be anywhere on drive. Normally efi partition should be near beginning of drive, but Windows often makes it the second or even third partition, but first one or two are smaller repair or utility partitions.

Grub menu can only boot other installs in the same boot mode or once you start booting in UEFI you cannot from grub boot a BIOS install. But you can boot from UEFI/BIOS or perhaps one time boot key installs in BIOS or UEFI.

Thanks again for the info,

I think I'm going to mark ths thread as solved. A lot of this is more a problem with Windows 7 installer since it doesn't want to format GPT partitions. So if you want to dual boot Win 7 in EFI mode using GPT partition table it seems like the best option is to use Gparted to partition the drive before installig Windows.

---

