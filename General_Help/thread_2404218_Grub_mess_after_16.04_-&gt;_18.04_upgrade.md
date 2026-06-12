---
title: "Grub mess after 16.04 -&gt; 18.04 upgrade"
date: 2018-10-21
forum: General Help
---

### Post by Koybe on 2018-10-21
Hello,

I have two hard disk, and I want to keep separate both Ubuntu and Windows 10.
When I did my first install I had Windows 10 on sdb and Ubuntu on sda device.
sdb has W10 bootloader
sda has Grub

After the upgrade, I don't know why because I don't get to choose, when i try to boot directly sdb, there is no operating system found... Windows should. 
When I boot on sda, i get to grub and I can start both system (Windows and Ubuntu).

But, I just want to boot from disk and not choose from grub... I don't know how to get there.

sudo fdisk -l
Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe78f7d11

Device     Boot    Start       End   Sectors  Size Id Type
/dev/sda1  *        2048  29296639  29294592   14G 83 Linux
/dev/sda2       29296640  48828415  19531776  9.3G 82 Linux swap / Solaris
/dev/sda3       48828416 234440703 185612288 88.5G 83 Linux


Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0A68025C-AB6E-40D3-AF56-CBAF0B3F4B7F

Device       Start       End   Sectors   Size Type
/dev/sdb1     2048    923647    921600   450M Windows recovery environment
/dev/sdb2   923648   1128447    204800   100M EFI System
/dev/sdb3  1128448   1161215     32768    16M Microsoft reserved
/dev/sdb4  1161216 976773119 975611904 465.2G Microsoft basic data


Any help welcome. Thanks.

---

### Post by ajgreeny on 2018-10-21
It will be best to see exactly where you are at present so go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by Koybe on 2018-10-22
Here it is sbc is not relevant, an old unused hard drive.

[https://paste.ubuntu.com/p/PsFf56sYpy/](https://paste.ubuntu.com/p/PsFf56sYpy/)

---

### Post by oldfred on 2018-10-22
UEFI and BIOS are not compatible, or once you start booting in one mode from UEFI, you cannot switch. Or grub only boots other systems installed in same boot mode as Ubuntu/grub is installed, UEFI or BIOS.

You have Windows installed to sda on a gpt partitioned drive for UEFI boot.
You have Ubuntu on a MBR partitioned drive for BIOS boot, but have an old BIOS Windows boot loader in MBR of sda. 
If you want to boot from UEFI, just add grub to MBR of sda. Do not run any auto fix from Boot-Repair, but use advanced mode and choose Ubuntu and sda drive.

You must have had grub's efi version installed into the Windows ESP on sdb. But UEFI highly recommends that you use gpt.
If you want to keep the now 35 year old MBR partitioning on sda, you can as Boot-Repair does seem to offer to install the UEFI boot version of grub to the ESP.
But I think Boot-Repair can do that, but a normal update of grub would not.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by Koybe on 2018-10-22
I must say I don't relay care about UEFI boot or classic BIOS. And I'm not sure to completely understand your advice.
All I want is booting Windows when I choose sdb from the bios and Ubuntu/Grub when I choose sda from bios.
That's what I had before upgrading to 18.04. (And I still wonder why did grub change anything, I asked for nothing).

---

### Post by oldfred on 2018-10-22
Then just install the BIOS boot version of grub to sda.
But it does look like you had a MBR partitioned drive for Ubuntu which with UEFI is very unusual and probably explains why upgrade did not work completely.
Boot-Repair also offers to reinstall the UEFI version of grub.

So depending on how you boot Ubuntu live installer and then use Boot-Repair it should offer to either install the UEFI version of grub to ESP on Windows drive or the BIOS version of grub to MBR of Ubuntu drive. 
If you install in BIOS mode, grub will not be able to boot Windows, but you should be able to boot from UEFI.

---

### Post by Koybe on 2018-10-23
Ok, Thanks!

---

