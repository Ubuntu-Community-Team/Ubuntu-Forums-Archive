---
title: "Install DD USB LVM Based Image Onto Hard Drive Partition for Dual Boot"
date: 2016-06-08
forum: General Help
---

### Post by Sylice on 2016-06-08
I realize it's a fairly specific question but I really hope someone can help me out with this, I have been trying to solve it on my own for days and getting nowhere.

Basically I have a hard drive with numerous partitions installed:
/dev/sda1  (boot partition)
/dev/sda2  (blank partition for the purpose of what I'm trying to do here)
/dev/sda3  (windows)
(and a few more after that).

Anyway, I have an DD image file that someone created specifically for a USB stick which if you write to the USB stick it creates a bootable stick with a pre-customized version of Lubuntu setup with an LVM configuration.

The LVM is 8gb with about 3.5gb of data in it.

Basically I'm trying to use DD to copy the data onto /dev/sda2 in a way that will be readable and can be booted.

I don't fully understand the LVM system as I have never used it before. I don't know if I'd be having so many problems if it wasn't for that, but anyway, with that said... I'm trying to setup a dual boot between Windows and this. Every DD line that I try copies the data over in some way where I can no longer access it (if I boot from another standad Ubuntu Live USB I can't seem to read the partition). GParted also says it can't read it after I've done the DD copy, so I'm obviously copying the data incorrectly or something else I'm not understanding due to the layout.

I've tried quite a number of DD commands.

Here is the display of fdisk -l when I have a copy of the USB that I'm trying to copy the image of to the main hard drive inserted:

```

[LIST]
[*][COLOR=#333333]Disk /dev/sda: 320.1 GB, 320072933376 bytes[/COLOR]
[*][COLOR=#333333]255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors[/COLOR]
[*][COLOR=#333333]Units = sectors of 1 * 512 = 512 bytes[/COLOR]
[*][COLOR=#333333]Sector size (logical/physical): 512 bytes / 512 bytes[/COLOR]
[*][COLOR=#333333]I/O size (minimum/optimal): 512 bytes / 512 bytes[/COLOR]
[*][COLOR=#333333]Disk identifier: 0x000bd149[/COLOR]
[*][COLOR=#333333]   Device Boot      Start         End      Blocks   Id  System[/COLOR]
[*][COLOR=#333333]/dev/sda1   *        2048     1050623      524288    7  HPFS/NTFS/exFAT[/COLOR]
[*][COLOR=#333333]/dev/sda2         1050624    42993663    20971520   83  Linux[/COLOR]
[*][COLOR=#333333]/dev/sda3        42993664   168822783    62914560    7  HPFS/NTFS/exFAT[/COLOR]
[*][COLOR=#333333]/dev/sda4       168824769   625141759   228158495+   f  W95 Ext'd (LBA)[/COLOR]
[*][COLOR=#333333]/dev/sda5       168824832   378540031   104857600    7  HPFS/NTFS/exFAT[/COLOR]
[*][COLOR=#333333]/dev/sda6       378542080   556799999    89128960   83  Linux[/COLOR]
[*][COLOR=#333333]/dev/sda7       556802048   591405055    17301504    7  HPFS/NTFS/exFAT[/COLOR]
[*][COLOR=#333333]/dev/sda8       591407104   625141759    16867328   82  Linux swap / Solaris[/COLOR]
[*][COLOR=#333333]Disk /dev/sdb: 7739 MB, 7739768832 bytes[/COLOR]
[*][COLOR=#333333]255 heads, 63 sectors/track, 940 cylinders, total 15116736 sectors[/COLOR]
[*][COLOR=#333333]Units = sectors of 1 * 512 = 512 bytes[/COLOR]
[*][COLOR=#333333]Sector size (logical/physical): 512 bytes / 512 bytes[/COLOR]
[*][COLOR=#333333]I/O size (minimum/optimal): 512 bytes / 512 bytes[/COLOR]
[*][COLOR=#333333]Disk identifier: 0x038f8180[/COLOR]
[*][COLOR=#333333]   Device Boot      Start         End      Blocks   Id  System[/COLOR]
[*][COLOR=#333333]/dev/sdb1   *        2048    15116735     7557344    c  W95 FAT32 (LBA)[/COLOR]
[*][COLOR=#333333]Disk /dev/sdc: 15.7 GB, 15728640000 bytes[/COLOR]
[*][COLOR=#333333]159 heads, 47 sectors/track, 4110 cylinders, total 30720000 sectors[/COLOR]
[*][COLOR=#333333]Units = sectors of 1 * 512 = 512 bytes[/COLOR]
[*][COLOR=#333333]Sector size (logical/physical): 512 bytes / 512 bytes[/COLOR]
[*][COLOR=#333333]I/O size (minimum/optimal): 512 bytes / 512 bytes[/COLOR]
[*][COLOR=#333333]Disk identifier: 0x00080285[/COLOR]
[*][COLOR=#333333]   Device Boot      Start         End      Blocks   Id  System[/COLOR]
[*][COLOR=#333333]/dev/sdc2   *        2048    15159295     7578624   8e  Linux LVM[/COLOR]
[*][COLOR=#333333]Disk /dev/mapper/root-root: 6442 MB, 6442450944 bytes[/COLOR]
[*][COLOR=#333333]255 heads, 63 sectors/track, 783 cylinders, total 12582912 sectors[/COLOR]
[*][COLOR=#333333]Units = sectors of 1 * 512 = 512 bytes[/COLOR]
[*][COLOR=#333333]Sector size (logical/physical): 512 bytes / 512 bytes[/COLOR]
[*][COLOR=#333333]I/O size (minimum/optimal): 512 bytes / 512 bytes[/COLOR]
[*][COLOR=#333333]Disk identifier: 0x00000000[/COLOR]
[*][COLOR=#333333]Disk /dev/mapper/root-root doesn't contain a valid partition table[/COLOR]
[/LIST]

```
( since that output may be difficult to read on the forum layout, I created a pastebin of it: [http://pastebin.com/RYBnkZ6b](http://pastebin.com/RYBnkZ6b) )

/sda is the main hard drive
/sdb is just the bootable Linux I'm on currently
/sdc contains the DD image already copied to another USB (that is also bootable and confirmed working but inserted separately afterwards)

I've tried simple dd commands such as:
dd if=/dev/sdc2 of /dev/sda2 bs=4k

as well as some with some additions like skipping the first 2048 blocks or using conv=sparse to use up the entire disk space (the partition is 20gb whereas the image is only an 8GB LVM).

I've used Gparted to format that partition as both LVM2, and/or EXT4 and tried the dd commands that way.

As you can probably tell I'm not terribly familiar with proper usage of DD either or the way these partitions are laid out.

I'm not sure if I could just simply use a recursive cp command to copy all the files from the USB to a preformated hard drive partition? I think I would lose proper system permissions if I was to do that because the user that comes preinstalled on the USB is different.

I'm not terribly concerned with the "booting" of the partition yet. I just need to get all the data moved over in a way that is readable. I presume if I can read it from within my Ubuntu Live USB then I can figure out configuring the Grub to boot off it but every method I've been trying to make an exact copy of this data to a readable partition on the main hard drive seems to be failing me.

Thoughts? Suggestions? What am I doing wrong?

And if anyone cares enough or needs access to the image I'm trying to do this all with, it is downloadable as a torrent and located here:
[https://ethereum-mining.info/genethos-bigfoot-edition%20-08_04_16.img.7z.torrent](https://ethereum-mining.info/genethos-bigfoot-edition%20-08_04_16.img.7z.torrent)  (zipped down to the 1 - 2gb range, img inside)

---

### Post by tenet75 on 2016-06-08
I've run into this before.  Check your fstab file to see if it uses UUIDs.  They need to be changed to match the new destination UUIDs.

---

### Post by oldfred on 2016-06-08
I do not know LVM, but it usually has a separate /boot partition. I do not see how your flash drive boots?
Does it work before you try copying it?

Any formatting or set up of partition before the dd automatically gets erases as dd copies bit for bit, so nothing is retained on partition from prior to copy.

Why LVM, or is it also encrypted?

Just to understand some of the details, you can run the Summary report:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Sylice on 2016-06-08
As to the reason of why LVM, I'm not 100% certain but I believe it is related to a preconfigured setup to allow this drive/device to cluster with other systems, but I don't know LVM a whole lot, I understand that it merges multiple physical drives into a single volume but I don't know much else about it or why the original creator of the system is using it specifically. For now I'm just trying to get this single instance of this working on a dual boot and will look into that clustering business later.

When I view the USB I made from this image in Gparted it only shows a single partition to me and it is listed same as it is in fdisk there on /sdc2

@Tenet75: there is a UUID in there but I can't access the fstab to change the UUID since after I do the dd copy it's unreadable :(

The USB boots itself so it must have a boot partition of some kind in there. The system will boot it with no hard drive whatsoever connected.

I do understand that DD copies the entire image bit for bit but certainly within that disk there is some sort of structure, like a boot sector in the first 512 bytes or whatever is standard for that.

I'm not sure how to list the layout of the USB (after it's been written) aside from looking in GParted or using fdisk -l as I've already done, is there some way I can get more useful data the layout to provide here?

---

### Post by oldfred on 2016-06-08
You cannot copy an entire drive into a partition and have anything useful. 
If you dd copy one partition to anther you get just the partition, but the flash drive must have some boot loader in the MBR and drivers for LVM.

Your installs or live systems will not normally have LVM drivers.
If you install them then you may be able to mount it.
sudo apt-get install lvm2

I am now curious on flash drive, but may not be able to tell much as never used LVM.
       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Sylice on 2016-06-08
[ATTACH=CONFIG]269480[/ATTACH]

Here is a GParted Screenshot. This thing boots up using standard GRUB.

I have no idea where partition 1 is.

---

### Post by oldfred on 2016-06-08
Syslinux is a Windows type boot loader that is used by Linux to repair Windows and is used to boot the installer in BIOS boot mode.

But it looks like it works with LVM, never knew that.
[http://www.syslinux.org/wiki/index.php?title=Development/LVM_support](http://www.syslinux.org/wiki/index.php?title=Development/LVM_support)

---

### Post by Sylice on 2016-06-08
Good to know on the SysLinux. At the moment I'm using the Windows bootloader and was planning to use NeoGrub to chainload a GRUB on the partition I am trying to copy over but if I have issues because its LVM this could be handy.

I don't think the booting will be too much of an issue though, I know Grub itself has an lvm module that can be loaded and I could just switch to that as my main loader and chainload Windows on another drive.

Just need to figure out how to get this partition copied in a format that's readable.

I'm sure I'm copying too much or the wrong blocks of data somehow. Since the image is basically an entire drive but I just want the LVM part of it. If I was to write the whole thing to a blank hard drive I'm sure it would work but trying to fit it into that one partition. There's got to be a way.

Anyone know of a tool that would allow me to view the structure of the original image?

This might be useful, will maybe give this a try tomorrow (Thursday), see if it gets me anywhere new: http://superuser.com/questions/117136/how-can-i-mount-a-partition-from-dd-created-image-of-a-block-device-e-g-hdd-u

---

### Post by Sylice on 2016-06-09
> **oldfred said:**
> Just to understand some of the details, you can run the Summary report:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

** @oldfred:** Sorry took a little longer to get back on and create the boot-info but I have done so. This is not on the final system that I am attempting to put this partition on, however I'm using this one as a test system as the other one is in production use currently. But anyway, if I can get it working on this system I'm quite confident I can get it working over there as well.

Here is the boot-info pastebin:
[URL="http://pastebin.com/u2nXjpXY"]http://pastebin.com/u2nXjpXY
[/URL]
I created this from within the actual LVM system, booted off the USB that it is written to (which is a customized Lubuntu).

And also pasted here if you prefer:
```
Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos4)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp ext2 part_msdos
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for 
    (lvmid/kdH4JF-uvrI-AdpX-LfKc-Xwlm-TLdd-fjTEjv/tJibfe-EwT6-91fm-QqcB-CvlP-ct
    KJ-AZEOa8)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos diskfilter lvm biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

root-root: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     1,050,623     1,048,576   7 NTFS / exFAT / HPFS
/dev/sda2           1,050,624    33,556,479    32,505,856  83 Linux
/dev/sda3    *     33,556,480   201,328,639   167,772,160   7 NTFS / exFAT / HPFS
/dev/sda4         201,328,640 1,250,263,039 1,048,934,400   5 Extended
/dev/sda5         201,330,688   578,818,047   377,487,360   7 NTFS / exFAT / HPFS
/dev/sda6         578,820,096 1,239,422,975   660,602,880   7 NTFS / exFAT / HPFS
/dev/sda7       1,239,425,024 1,250,263,039    10,838,016  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   104,859,647   104,857,600   7 NTFS / exFAT / HPFS
/dev/sdb2         104,859,648   188,745,727    83,886,080   7 NTFS / exFAT / HPFS
/dev/sdb3         188,745,728   469,764,095   281,018,368   7 NTFS / exFAT / HPFS
/dev/sdb4         469,764,096   488,396,799    18,632,704  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 15.7 GB, 15728640000 bytes
159 heads, 47 sectors/track, 4110 cylinders, total 30720000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc2    *          2,048    15,159,295    15,157,248  8e Linux LVM


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/root-root 9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5   ext4       
/dev/sda1        0B9B5C8703ED7B16                       ntfs       boot
/dev/sda2        cb38720e-4bc9-4c51-9eb6-640ba1924e2a   ext4       
/dev/sda3        E6DCEBB8DCEB8163                       ntfs       Win10
/dev/sda5        52CEBF74CEBF4F4B                       ntfs       Data
/dev/sda6        3C5C87805C873424                       ntfs       Games
/dev/sda7        75013a0c-81f5-42b7-9e34-a87ab00eb530   swap       
/dev/sdb1        0832795F327952A4                       ntfs       Win7Old
/dev/sdb2        2C727EC8727E95F4                       ntfs       DataOld
/dev/sdb3        FA3A82B33A826D07                       ntfs       GamesOld
/dev/sdb4        360f2286-e3e9-4fd2-8324-0f54f8eccddd   ext4       
/dev/sdc2        Ywwztv-MGOT-dIdb-soXU-vyou-knLF-RSbdrL LVM2_member 

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jun  9 12:25 ata-HDT722525DLA380_VDB41BT4F0GG9C -> ../../sdb
lrwxrwxrwx 1 root root 10 Jun  9 12:42 ata-HDT722525DLA380_VDB41BT4F0GG9C-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jun  9 12:42 ata-HDT722525DLA380_VDB41BT4F0GG9C-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Jun  9 12:42 ata-HDT722525DLA380_VDB41BT4F0GG9C-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 Jun  9 12:26 ata-HDT722525DLA380_VDB41BT4F0GG9C-part4 -> ../../sdb4
lrwxrwxrwx 1 root root  9 Jun  9 12:25 ata-HL-DT-STDVD-RAM_GSA-H55N -> ../../sr0
lrwxrwxrwx 1 root root  9 Jun  9 12:25 ata-WDC_WD6401AALS-00L3B2_WD-WMASY3451577 -> ../../sda
lrwxrwxrwx 1 root root 10 Jun  9 12:25 ata-WDC_WD6401AALS-00L3B2_WD-WMASY3451577-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jun  9 12:25 ata-WDC_WD6401AALS-00L3B2_WD-WMASY3451577-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jun  9 12:42 ata-WDC_WD6401AALS-00L3B2_WD-WMASY3451577-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jun  9 12:25 ata-WDC_WD6401AALS-00L3B2_WD-WMASY3451577-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jun  9 12:42 ata-WDC_WD6401AALS-00L3B2_WD-WMASY3451577-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jun  9 12:42 ata-WDC_WD6401AALS-00L3B2_WD-WMASY3451577-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Jun  9 12:26 ata-WDC_WD6401AALS-00L3B2_WD-WMASY3451577-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Jun  9 12:41 dm-name-root-root -> ../../dm-0
lrwxrwxrwx 1 root root 10 Jun  9 12:41 dm-uuid-LVM-kdH4JFuvrIAdpXLfKcXwlmTLddfjTEjvtJibfeEwT691fmQqcBCvlPctKJAZEOa8 -> ../../dm-0
lrwxrwxrwx 1 root root  9 Jun  9 12:41 usb-Kingston_DataTraveler_3.0_08606E6B6615BE10734546EA-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 Jun  9 12:26 usb-Kingston_DataTraveler_3.0_08606E6B6615BE10734546EA-0:0-part2 -> ../../sdc2
lrwxrwxrwx 1 root root  9 Jun  9 12:25 wwn-0x5000cca20bea7ccc -> ../../sdb
lrwxrwxrwx 1 root root 10 Jun  9 12:42 wwn-0x5000cca20bea7ccc-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jun  9 12:42 wwn-0x5000cca20bea7ccc-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Jun  9 12:42 wwn-0x5000cca20bea7ccc-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 Jun  9 12:26 wwn-0x5000cca20bea7ccc-part4 -> ../../sdb4
lrwxrwxrwx 1 root root  9 Jun  9 12:25 wwn-0x50014ee000d838b6 -> ../../sda
lrwxrwxrwx 1 root root 10 Jun  9 12:25 wwn-0x50014ee000d838b6-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jun  9 12:25 wwn-0x50014ee000d838b6-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jun  9 12:42 wwn-0x50014ee000d838b6-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jun  9 12:25 wwn-0x50014ee000d838b6-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jun  9 12:42 wwn-0x50014ee000d838b6-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jun  9 12:42 wwn-0x50014ee000d838b6-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Jun  9 12:26 wwn-0x50014ee000d838b6-part7 -> ../../sda7

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
root-root

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/root-root /                        ext4       (rw,noatime,errors=remount-ro)


=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="5"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  cb38720e-4bc9-4c51-9eb6-640ba1924e2a
else
  search --no-floppy --fs-uuid --set=root cb38720e-4bc9-4c51-9eb6-640ba1924e2a
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_CA
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-cb38720e-4bc9-4c51-9eb6-640ba1924e2a' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  cb38720e-4bc9-4c51-9eb6-640ba1924e2a
    else
      search --no-floppy --fs-uuid --set=root cb38720e-4bc9-4c51-9eb6-640ba1924e2a
    fi
    linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=cb38720e-4bc9-4c51-9eb6-640ba1924e2a ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-22-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-cb38720e-4bc9-4c51-9eb6-640ba1924e2a' {
    menuentry 'Ubuntu, with Linux 4.4.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-22-generic-advanced-cb38720e-4bc9-4c51-9eb6-640ba1924e2a' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  cb38720e-4bc9-4c51-9eb6-640ba1924e2a
        else
          search --no-floppy --fs-uuid --set=root cb38720e-4bc9-4c51-9eb6-640ba1924e2a
        fi
        echo    'Loading Linux 4.4.0-22-generic ...'
        linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=cb38720e-4bc9-4c51-9eb6-640ba1924e2a ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-22-generic-recovery-cb38720e-4bc9-4c51-9eb6-640ba1924e2a' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  cb38720e-4bc9-4c51-9eb6-640ba1924e2a
        else
          search --no-floppy --fs-uuid --set=root cb38720e-4bc9-4c51-9eb6-640ba1924e2a
        fi
        echo    'Loading Linux 4.4.0-22-generic ...'
        linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=cb38720e-4bc9-4c51-9eb6-640ba1924e2a ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-advanced-cb38720e-4bc9-4c51-9eb6-640ba1924e2a' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  cb38720e-4bc9-4c51-9eb6-640ba1924e2a
        else
          search --no-floppy --fs-uuid --set=root cb38720e-4bc9-4c51-9eb6-640ba1924e2a
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=cb38720e-4bc9-4c51-9eb6-640ba1924e2a ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-recovery-cb38720e-4bc9-4c51-9eb6-640ba1924e2a' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  cb38720e-4bc9-4c51-9eb6-640ba1924e2a
        else
          search --no-floppy --fs-uuid --set=root cb38720e-4bc9-4c51-9eb6-640ba1924e2a
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=cb38720e-4bc9-4c51-9eb6-640ba1924e2a ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  cb38720e-4bc9-4c51-9eb6-640ba1924e2a
    else
      search --no-floppy --fs-uuid --set=root cb38720e-4bc9-4c51-9eb6-640ba1924e2a
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  cb38720e-4bc9-4c51-9eb6-640ba1924e2a
    else
      search --no-floppy --fs-uuid --set=root cb38720e-4bc9-4c51-9eb6-640ba1924e2a
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 10 (loader) (on /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-chain-E6DCEBB8DCEB8163' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  E6DCEBB8DCEB8163
    else
      search --no-floppy --fs-uuid --set=root E6DCEBB8DCEB8163
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-0832795F327952A4' {
    insmod part_msdos
    insmod ntfs
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  0832795F327952A4
    else
      search --no-floppy --fs-uuid --set=root 0832795F327952A4
    fi
    parttool ${root} hidden-
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=cb38720e-4bc9-4c51-9eb6-640ba1924e2a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=75013a0c-81f5-42b7-9e34-a87ab00eb530 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   8.739410400 = 9.383870464    boot/grub/grub.cfg                             1
  12.630477905 = 13.561872384   boot/grub/i386-pc/core.img                     1
   1.284851074 = 1.379598336    boot/vmlinuz-4.4.0-21-generic                  1
   2.346328735 = 2.519351296    boot/vmlinuz-4.4.0-22-generic                  1
   2.346328735 = 2.519351296    vmlinuz                                        1
   1.284851074 = 1.379598336    vmlinuz.old                                    1
  13.329097748 = 14.312009728   boot/initrd.img-4.4.0-21-generic               2
   0.801185608 = 0.860266496    boot/initrd.img-4.4.0-22-generic               1
   0.801185608 = 0.860266496    initrd.img                                     1
  13.329097748 = 14.312009728   initrd.img.old                                 2

======================== root-root/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  # GRUB lacks write support for lvm, so recordfail support is disabled.
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod lvm
insmod ext2
set root='lvmid/kdH4JF-uvrI-AdpX-LfKc-Xwlm-TLdd-fjTEjv/tJibfe-EwT6-91fm-QqcB-CvlP-ctKJ-AZEOa8'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint='lvmid/kdH4JF-uvrI-AdpX-LfKc-Xwlm-TLdd-fjTEjv/tJibfe-EwT6-91fm-QqcB-CvlP-ctKJ-AZEOa8'  9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5
else
  search --no-floppy --fs-uuid --set=root 9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=2
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=2
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod lvm
    insmod ext2
    set root='lvmid/kdH4JF-uvrI-AdpX-LfKc-Xwlm-TLdd-fjTEjv/tJibfe-EwT6-91fm-QqcB-CvlP-ctKJ-AZEOa8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint='lvmid/kdH4JF-uvrI-AdpX-LfKc-Xwlm-TLdd-fjTEjv/tJibfe-EwT6-91fm-QqcB-CvlP-ctKJ-AZEOa8'  9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5
    else
      search --no-floppy --fs-uuid --set=root 9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5
    fi
    linux    /boot/vmlinuz-4.2.0-35-generic root=/dev/mapper/root-root ro  quiet nosplash nogpumanager locale=ru_RU.UTF-8
    initrd    /boot/initrd.img-4.2.0-35-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5' {
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-advanced-9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod lvm
        insmod ext2
        set root='lvmid/kdH4JF-uvrI-AdpX-LfKc-Xwlm-TLdd-fjTEjv/tJibfe-EwT6-91fm-QqcB-CvlP-ctKJ-AZEOa8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint='lvmid/kdH4JF-uvrI-AdpX-LfKc-Xwlm-TLdd-fjTEjv/tJibfe-EwT6-91fm-QqcB-CvlP-ctKJ-AZEOa8'  9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5
        else
          search --no-floppy --fs-uuid --set=root 9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=/dev/mapper/root-root ro  quiet nosplash nogpumanager locale=ru_RU.UTF-8
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-recovery-9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod lvm
        insmod ext2
        set root='lvmid/kdH4JF-uvrI-AdpX-LfKc-Xwlm-TLdd-fjTEjv/tJibfe-EwT6-91fm-QqcB-CvlP-ctKJ-AZEOa8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint='lvmid/kdH4JF-uvrI-AdpX-LfKc-Xwlm-TLdd-fjTEjv/tJibfe-EwT6-91fm-QqcB-CvlP-ctKJ-AZEOa8'  9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5
        else
          search --no-floppy --fs-uuid --set=root 9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=/dev/mapper/root-root ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod lvm
    insmod ext2
    set root='lvmid/kdH4JF-uvrI-AdpX-LfKc-Xwlm-TLdd-fjTEjv/tJibfe-EwT6-91fm-QqcB-CvlP-ctKJ-AZEOa8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint='lvmid/kdH4JF-uvrI-AdpX-LfKc-Xwlm-TLdd-fjTEjv/tJibfe-EwT6-91fm-QqcB-CvlP-ctKJ-AZEOa8'  9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5
    else
      search --no-floppy --fs-uuid --set=root 9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod lvm
    insmod ext2
    set root='lvmid/kdH4JF-uvrI-AdpX-LfKc-Xwlm-TLdd-fjTEjv/tJibfe-EwT6-91fm-QqcB-CvlP-ctKJ-AZEOa8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint='lvmid/kdH4JF-uvrI-AdpX-LfKc-Xwlm-TLdd-fjTEjv/tJibfe-EwT6-91fm-QqcB-CvlP-ctKJ-AZEOa8'  9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5
    else
      search --no-floppy --fs-uuid --set=root 9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

============================= root-root/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5 /               ext4    noatime,errors=remount-ro 0       1
tmpfs   /var/cache/apt/archives tmpfs   defaults        0       0
tmpfs /var/log tmpfs defaults 0 0
tmpfs /tmp tmpfs defaults 0 0
--------------------------------------------------------------------------------

================= root-root: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

   2.820491791 = 3.028480000    boot/grub/grub.cfg                             1
   0.171005249 = 0.183615488    boot/grub/i386-pc/core.img                     1
   4.838298798 = 5.195083776    boot/vmlinuz-4.2.0-35-generic                  2
   4.838298798 = 5.195083776    vmlinuz                                        2
   5.359371185 = 5.754580992    boot/initrd.img-4.2.0-35-generic               2
   5.359371185 = 5.754580992    initrd.img                                     2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  25 ff 57 6c 3c 7f 5f fb  11 5e 9f 68 fc 67 e8 70  |%.Wl<._..^.h.g.p|
00000010  2f cc e8 f3 a8 f0 bf 5f  e3 f8 39 41 60 1d 8b d9  |/......_..9A`...|
00000020  2f 04 fe e9 12 88 ff a7  9e 05 f8 ff fb 7f b9 21  |/..............!|
00000030  e2 bf ac 9e 97 d0 ff 88  cf eb a3 14 2f 8b 7c 3f  |............/.|?|
00000040  84 7f b5 3e c4 bf 89 f1  e4 4b da 6c c4 0b f1 bf  |...>.....K.l....|
00000050  41 fa 9d f1 7f 29 1a eb  e7 71 e9 9f cb 82 9f 87  |A....)...q......|
00000060  06 9b 2a be e8 f5 fc d3  00 89 c5 93 ac 17 07 fa  |..*.............|
00000070  c3 95 ed 35 9e 8f f0 9f  6d 85 bc de 8b e7 e8 f9  |...5....m.......|
00000080  05 88 7f 4a 66 6a 9c cf  9c e9 a3 f9 40 7f da 96  |...Jfj......@...|
00000090  9a 7f 43 8f ad d3 6a 7e  de 2f c2 bf 81 fa ff d4  |..C...j~./......|
000000a0  09 8a 2f 01 c7 c7 5e 93  92 c9 5c 1d f8 ff 91 d2  |../...^...\.....|
000000b0  7b c7 18 ff 74 38 32 bc  5f 1b 0f 3d 73 d7 e1 e7  |{...t82._..=s...|
000000c0  f9 b7 75 fa 1c f4 74 17  fe 3f 90 ff 13 ff eb fd  |..u...t..?......|
000000d0  7d 70 3f 66 ef d5 7c 0f  f8 df 42 bc 94 8a b5 6c  |}p?f..|...B....l|
000000e0  2b e0 78 5c 5c 5e 9a 8a  97 11 ff 35 73 cc e1 e7  |+.x\\^.....5s...|
000000f0  a3 f8 df 13 fc 1f 98 98  bf 29 fe 27 fe d2 eb cd  |.........).'....|
00000100  cd d5 b2 cf 97 66 f4 79  9a 9b 0d 28 ff b7 9e 33  |.....f.y...(...3|
00000110  fe 4b f5 b7 07 02 ff 7e  0a f0 f6 21 fd ff 14 f4  |.K.....~...!....|
00000120  89 c2 3f fa 19 7e 26 24  fc 5b 7a 3d 99 09 47 e1  |..?..~&$.[z=..G.|
00000130  5f 5f 7f 22 45 c1 30 c6  f1 e8 48 ff eb 71 32 41  |__."E.0...H..q2A|
00000140  c9 75 c8 e7 9f f8 bf 90  fe bb c4 7f ba c2 fc 7c  |.u.............||
00000150  88 7f de bf eb 57 89 ec  ca ec cf 74 f3 7f d8 a9  |.....W.....t....|
00000160  ff 0b c8 cf 0a ff c8 a7  a4 ff cd 7d c7 d7 f8 54  |...........}...T|
00000170  fa 1f fd 06 e2 7f d2 03  8b 92 ff 7f a9 ea 31 e9  |..............1.|
00000180  ff 97 ee 34 eb 81 08 ff  01 e7 97 17 cf 29 7e e6  |...4.........)~.|
00000190  fd 39 7f 46 f1 0f e7 73  67 fa e8 70 0a fc 67 44  |.9.F...sg..p..gD|
000001a0  3c 20 fd 4f f7 b3 a2 f7  e3 1f 4f ad 6d b8 10 9f  |< .O......O.m...|
000001b0  88 ff cd 74 90 05 fe a7  fc ae 6c c4 19 ff 00 fe  |...t......l.....|
000001c0  ff ff 07 fe ff ff 00 08  00 00 00 00 80 16 00 03  |................|
000001d0  c5 ff 05 fe ff ff 00 08  80 16 00 08 60 27 00 00  |............`'..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/5914/mounts) leaked on lvs invocation. Parent PID 19241: bash
File descriptor 63 (pipe:[25921]) leaked on lvs invocation. Parent PID 19241: bash
File descriptor 9 (/proc/5914/mounts) leaked on lvchange invocation. Parent PID 21736: bash
File descriptor 63 (pipe:[25921]) leaked on lvchange invocation. Parent PID 21736: bash

ADDITIONAL INFORMATION :
=================== log of boot-info 2016-06-09__12h41 ===================
boot-info version : 4ppa37
boot-sav version : 4ppa37
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa37
BLKID BEFORE LVM ACTIVATION:
/dev/sda1: LABEL="boot" UUID="0B9B5C8703ED7B16" TYPE="ntfs"
/dev/sda2: UUID="cb38720e-4bc9-4c51-9eb6-640ba1924e2a" TYPE="ext4"
/dev/sda3: LABEL="Win10" UUID="E6DCEBB8DCEB8163" TYPE="ntfs"
/dev/sda5: LABEL="Data" UUID="52CEBF74CEBF4F4B" TYPE="ntfs"
/dev/sda6: LABEL="Games" UUID="3C5C87805C873424" TYPE="ntfs"
/dev/sda7: UUID="75013a0c-81f5-42b7-9e34-a87ab00eb530" TYPE="swap"
/dev/sdb1: LABEL="Win7Old" UUID="0832795F327952A4" TYPE="ntfs"
/dev/sdb2: LABEL="DataOld" UUID="2C727EC8727E95F4" TYPE="ntfs"
/dev/sdb3: LABEL="GamesOld" UUID="FA3A82B33A826D07" TYPE="ntfs"
/dev/sdb4: UUID="360f2286-e3e9-4fd2-8324-0f54f8eccddd" TYPE="ext4"
/dev/sdc2: UUID="Ywwztv-MGOT-dIdb-soXU-vyou-knLF-RSbdrL" TYPE="LVM2_member"
/dev/mapper/root-root: UUID="9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5" TYPE="ext4"
MODPROBE
VGSCAN
File descriptor 9 (/proc/5914/mounts) leaked on vgscan invocation. Parent PID 5926: /bin/bash
Reading all physical volumes.  This may take a while...
Found volume group "root" using metadata type lvm2
VGCHANGE
File descriptor 9 (/proc/5914/mounts) leaked on vgchange invocation. Parent PID 5926: /bin/bash
1 logical volume(s) in volume group "root" now active
File descriptor 9 (/proc/5914/mounts) leaked on lvscan invocation. Parent PID 5926: /bin/bash
LVSCAN:
ACTIVE            '/dev/root/root' [6.00 GiB] inherit
Is there RAID on this computer? no
File descriptor 9 (/proc/5914/mounts) leaked on lvs invocation. Parent PID 7566: /bin/sh
boot-info is executed in installed-session (Ubuntu 14.04.4 LTS, trusty, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-4.2.0-35-generic root=/dev/mapper/root-root ro quiet nosplash nogpumanager locale=ru_RU.UTF-8
Set sda as corresponding disk of mapper/root-root
Set sda as corresponding disk of mapper/root-root
Disk /dev/mapper/root-root doesn't contain a valid partition table

=================== os-prober:
/dev/dm-0:The OS now in use - Ubuntu 14.04.4 LTS CurrentSession:linux
/dev/sda2:Ubuntu 16.04 LTS (16.04):Ubuntu:linux
/dev/sda3:Windows 10 (loader):Windows:chain
/dev/sdb1:Windows 7 (loader):Windows1:chain

=================== blkid:
/dev/sda1: LABEL="boot" UUID="0B9B5C8703ED7B16" TYPE="ntfs"
/dev/sda2: UUID="cb38720e-4bc9-4c51-9eb6-640ba1924e2a" TYPE="ext4"
/dev/sda3: LABEL="Win10" UUID="E6DCEBB8DCEB8163" TYPE="ntfs"
/dev/sda5: LABEL="Data" UUID="52CEBF74CEBF4F4B" TYPE="ntfs"
/dev/sda6: LABEL="Games" UUID="3C5C87805C873424" TYPE="ntfs"
/dev/sda7: UUID="75013a0c-81f5-42b7-9e34-a87ab00eb530" TYPE="swap"
/dev/sdb1: LABEL="Win7Old" UUID="0832795F327952A4" TYPE="ntfs"
/dev/sdb2: LABEL="DataOld" UUID="2C727EC8727E95F4" TYPE="ntfs"
/dev/sdb3: LABEL="GamesOld" UUID="FA3A82B33A826D07" TYPE="ntfs"
/dev/sdb4: UUID="360f2286-e3e9-4fd2-8324-0f54f8eccddd" TYPE="ext4"
/dev/sdc2: UUID="Ywwztv-MGOT-dIdb-soXU-vyou-knLF-RSbdrL" TYPE="LVM2_member"
/dev/mapper/root-root: UUID="9a7e2b1d-5f8b-4e1c-9972-1caa9b1a94e5" TYPE="ext4"

dm-0 (sda) has unknown type. Please report this message to boot.repair@gmail.com

2 disks with OS, 4 OS : 2 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

Linux not detected by os-prober on mapper/root-root. Please report this message to boot.repair@gmail.com
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== sda2/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Apr 20 18:15 grub.d
total 76
-rwxr-xr-x 1 root root  9791 Apr 15 18:00 00_header
-rwxr-xr-x 1 root root  6258 Mar 15 14:08 05_debian_theme
-rwxr-xr-x 1 root root 12261 Apr 15 18:00 10_linux
-rwxr-xr-x 1 root root 11082 Apr 15 18:00 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28 07:44 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr 15 18:00 30_os-prober
-rwxr-xr-x 1 root root  1418 Apr 15 18:00 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr 15 18:00 40_custom
-rwxr-xr-x 1 root root   216 Apr 15 18:00 41_custom
-rw-r--r-- 1 root root   483 Apr 15 18:00 README




=================== sda2/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=5
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== //etc/grub.d/ :
drwxr-xr-x   2 root root     4096 Jan 27 13:09 grub.d
total 76
-rwxr-xr-x 1 root root  9791 Dec 17 10:00 00_header
-rwxr-xr-x 1 root root  6058 May 13  2015 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 13  2015 10_linux
-rwxr-xr-x 1 root root 10412 May 13  2015 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 May 13  2015 30_os-prober
-rwxr-xr-x 1 root root  1416 May 13  2015 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 13  2015 40_custom
-rwxr-xr-x 1 root root   216 May 13  2015 41_custom
-rw-r--r-- 1 root root   483 May 13  2015 README




=================== //etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet nosplash nogpumanager locale=ru_RU.UTF-8"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== UEFI/Legacy mode:
This installed-session is not in EFI-mode.
SecureBoot disabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.
sda6    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda6.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdb1.
sdb2    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdb2.
sdb3    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb3.
sdb4    : sdb,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb4.
mapper/root-root    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD6401AALS-0 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  538MB   537MB   primary   ntfs
2      538MB   17.2GB  16.6GB  primary   ext4
3      17.2GB  103GB   85.9GB  primary   ntfs            boot
4      103GB   640GB   537GB   extended
5      103GB   296GB   193GB   logical   ntfs
6      296GB   635GB   338GB   logical   ntfs
7      635GB   640GB   5549MB  logical   linux-swap(v1)


Model: ATA HDT722525DLA380 (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  53.7GB  53.7GB  primary  ntfs         boot
2      53.7GB  96.6GB  42.9GB  primary  ntfs
3      96.6GB  241GB   144GB   primary  ntfs
4      241GB   250GB   9540MB  primary  ext4


Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdc: 15.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
2      1049kB  7762MB  7761MB  primary               boot, lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/root-root: 6442MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
1      0.00B  6442MB  6442MB  ext4

=================== parted -lm:

BYT;
/dev/sda:640GB:scsi:512:512:msdos:ATA WDC WD6401AALS-0;
1:1049kB:538MB:537MB:ntfs::;
2:538MB:17.2GB:16.6GB:ext4::;
3:17.2GB:103GB:85.9GB:ntfs::boot;
4:103GB:640GB:537GB:::;
5:103GB:296GB:193GB:ntfs::;
6:296GB:635GB:338GB:ntfs::;
7:635GB:640GB:5549MB:linux-swap(v1)::;

BYT;
/dev/sdb:250GB:scsi:512:512:msdos:ATA HDT722525DLA380;
1:1049kB:53.7GB:53.7GB:ntfs::boot;
2:53.7GB:96.6GB:42.9GB:ntfs::;
3:96.6GB:241GB:144GB:ntfs::;
4:241GB:250GB:9540MB:ext4::;

BYT;
/dev/sdc:15.7GB:scsi:512:512:msdos:Kingston DataTraveler 3.0;
2:1049kB:7762MB:7761MB:::boot, lvm;

BYT;
/dev/mapper/root-root:6442MB:dm:512:512:loop:Linux device-mapper (linear);
1:0.00B:6442MB:6442MB:ext4::;

=================== lsblk:
KNAME TYPE FSTYPE        SIZE LABEL
sda   disk             596.2G
sda1  part ntfs          512M boot
sda2  part ext4         15.5G
sda3  part ntfs           80G Win10
sda4  part                 1K
sda5  part ntfs          180G Data
sda6  part ntfs          315G Games
sda7  part swap          5.2G
sdb   disk             232.9G
sdb1  part ntfs           50G Win7Old
sdb2  part ntfs           40G DataOld
sdb3  part ntfs          134G GamesOld
sdb4  part ext4          8.9G
sdc   disk              14.7G
sdc2  part LVM2_member   7.2G
dm-0  lvm  ext4            6G
sr0   rom               1024M

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0         /mnt/boot-sav/sda2
sda3     1  0  0         /mnt/boot-sav/sda3
sda4     1  0  0
sda5     1  0  0         /mnt/boot-sav/sda5
sda6     1  0  0         /mnt/boot-sav/sda6
sda7     1  0  0
sdb      1  0  0 running
sdb1     1  0  0         /mnt/boot-sav/sdb1
sdb2     1  0  0         /mnt/boot-sav/sdb2
sdb3     1  0  0         /mnt/boot-sav/sdb3
sdb4     1  0  0         /mnt/boot-sav/sdb4
sdc      1  0  1 running
sdc2     1  0  1
dm-0     1  0  0 running /
sr0      1  0  1 running


=================== mount:
/dev/mapper/root-root on / type ext4 (rw,noatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /tmp type tmpfs (rw)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
tmpfs on /var/cache/apt/archives type tmpfs (rw)
tmpfs on /var/log type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /home/work/.gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=work)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type ext4 (rw)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /mnt/boot-sav/sda6 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb2 on /mnt/boot-sav/sdb2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb3 on /mnt/boot-sav/sdb3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb4 on /mnt/boot-sav/sdb4 type ext4 (rw)


=================== ls:
/sys/block/dm-0 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 sdb4 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc2 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  ati autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dm-0 ecryptfs fb0 fd full fuse fw0 hidraw0 hidraw1 hidraw2 hpet hwrng input kmsg kvm log mapper mcelog mem memory_bandwidth ndctl0 net network_latency network_throughput null port ppp psaux ptmx pts random rfkill root rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sdb sdb1 sdb2 sdb3 sdb4 sdc sdc2 sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom vfio vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control root-root

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff ff 0f 00 00 00 00 00  |................|
00000030  04 00 00 00 00 00 00 00  ff ff 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  16 7b ed 03 87 5c 9b 0b  |.........{.....|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 02  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff ff ff 09 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  63 81 eb dc b8 eb dc e6  |........c.......|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff ff 7f 16 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  4b 4f bf ce 74 bf ce 52  |........KO..t..R|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sda6
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 20 00 00  |.R.NTFS    .. ..|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff ff 5f 27 00 00 00 00  |.........._'....|
00000030  00 00 03 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 f4 00 00 00  24 34 87 5c 80 87 5c 3c  |........$4...<|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff ff 3f 06 00 00 00 00  |..........?.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  a4 52 79 32 5f 79 32 08  |.........Ry2_y2.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sdb2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 40 06  |........?.....@.|
00000020  00 00 00 00 80 00 80 00  ff ff ff 04 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  f4 95 7e 72 c8 7e 72 2c  |..........~r.~r,|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sdb3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 40 0b  |........?.....@.|
00000020  00 00 00 00 80 00 80 00  f8 ff bf 10 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  07 6d 82 3a b3 82 3a fa  |.........m.:..:.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200
Disk /dev/mapper/root-root doesn't contain a valid partition table

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs     799M  1.3M  797M   1% /run
/dev/dm-0      ext4      5.8G  2.8G  2.8G  51% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs     3.9G   16K  3.9G   1% /tmp
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     3.9G     0  3.9G   0% /run/shm
none           tmpfs     100M     0  100M   0% /run/user
tmpfs          tmpfs     3.9G   18M  3.9G   1% /var/cache/apt/archives
tmpfs          tmpfs     3.9G  2.7M  3.9G   1% /var/log
/dev/sda1      fuseblk   512M   38M  475M   8% /mnt/boot-sav/sda1
/dev/sda2      ext4       16G  3.4G   11G  24% /mnt/boot-sav/sda2
/dev/sda3      fuseblk    80G   16G   65G  20% /mnt/boot-sav/sda3
/dev/sda5      fuseblk   180G   22G  159G  13% /mnt/boot-sav/sda5
/dev/sda6      fuseblk   315G   99G  217G  32% /mnt/boot-sav/sda6
/dev/sdb1      fuseblk    50G   38G   13G  76% /mnt/boot-sav/sdb1
/dev/sdb2      fuseblk    40G   35G  6.0G  86% /mnt/boot-sav/sdb2
/dev/sdb3      fuseblk   134G   88G   47G  66% /mnt/boot-sav/sdb3
/dev/sdb4      ext4      8.7G   20M  8.2G   1% /mnt/boot-sav/sdb4

=================== fdisk -l:

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe3b884ae

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     1050623      524288    7  HPFS/NTFS/exFAT
/dev/sda2         1050624    33556479    16252928   83  Linux
/dev/sda3   *    33556480   201328639    83886080    7  HPFS/NTFS/exFAT
/dev/sda4       201328640  1250263039   524467200    5  Extended
/dev/sda5       201330688   578818047   188743680    7  HPFS/NTFS/exFAT
/dev/sda6       578820096  1239422975   330301440    7  HPFS/NTFS/exFAT
/dev/sda7      1239425024  1250263039     5419008   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe54a0fcb

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   104859647    52428800    7  HPFS/NTFS/exFAT
/dev/sdb2       104859648   188745727    41943040    7  HPFS/NTFS/exFAT
/dev/sdb3       188745728   469764095   140509184    7  HPFS/NTFS/exFAT
/dev/sdb4       469764096   488396799     9316352   83  Linux

Disk /dev/sdc: 15.7 GB, 15728640000 bytes
159 heads, 47 sectors/track, 4110 cylinders, total 30720000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00080285

Device Boot      Start         End      Blocks   Id  System
/dev/sdc2   *        2048    15159295     7578624   8e  Linux LVM

Disk /dev/mapper/root-root: 6442 MB, 6442450944 bytes
255 heads, 63 sectors/track, 783 cylinders, total 12582912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


User choice: Is sda (640GB) a removable disk? no




=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to enable-lvm) and reinstall the grub2 of sda2 into the MBRs of all disks (except USB without OS).
Additional repair would be performed: unhide-bootmenu-10s


=================== Blockers in case of suggested repair
Please use this software in a live-session (live-CD or live-USB). This will enable this feature.


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda (640GB) disk!


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by Sylice on 2016-06-09
I actually think I'm getting fairly close here.

So what I've just done is booted up into the system's Lubuntu that I have installed separately.

From there I mounted the genethos dd image file that I have and connected to the system as an lvm volume.

Then used dd to copy all data bit for bit from the lvm volume over to an ext4 formated partition I have empty on the system for this purpose.

The data finally seems to be readable... now I just need to configure my grub to boot it and see if it actually works or if by removing the LVM I have messed something up.

Here are the commands I have run to get this far:

```
# attaches the contents within the image file to /dev/loop0 (where 'genethos.img' is the filename of your image)
losetup --partscan --find --show genethos.img

#reports information about physical (lvm) volumes so you know where to use "vgchange"
pvs

# where 'vg' is the name of the volume group listed by running pvs above
# (vgchange  modifies attributes of a volume group, in this case we are using the "attach" parameter)
vgchange -a y vg

# this is all you need to do, you can how use dd to copy data directly from
# /dev/vg/vg_root
# with the path above being whatever your actual volume group parameters are (for me it was just root & root)

# then run to copy all data byte for byte to another partition of any kind, i.e. over to an ext4 partition
dd if=/dev/root/root of=/dev/sdb4 bs=8M status=progress
```

Also once this is done, if the partition is larger than the dd/lvm volume as it is in my case a:
resize2fs -p /dev/sdb4
needs to be executed

Much credit to the following websites for making it this far:
[http://www.utilities-online.info/articles/Mount-an-LVM-partition-image-cloned-with-dd/](http://www.utilities-online.info/articles/Mount-an-LVM-partition-image-cloned-with-dd/)
[http://daniel-albuschat.blogspot.ca/2008/02/converting-lvm-to-normal-partition.html](http://daniel-albuschat.blogspot.ca/2008/02/converting-lvm-to-normal-partition.html)

---

### Post by oldfred on 2016-06-09
Your grub2 installed in sdc's MBR, shows embedded lvm driver. So then that is how it manages to work.

---

### Post by Sylice on 2016-06-09
Makes sense. And with that said. I have finally met some solid success.

The attempt in my previous post to copy the files to ext4, well, it worked in that the files were then readable, but editing my on system GRUB to boot off that wasn't working. So I tried a new method to copy it as it's original LVM format.

Used GParted to format drive as LVM (may not have been necessary).

Used the previous command to attached the image to loop0 as follows:
losetup --partscan --find --show genethos.img

This allowed access to the second lvm partition at:
/dev/loop0p2

Attached the image file I have with the LVM driver in Linux as before using (not sure if this was necessary):
vgchange -a y root

(root is the name of the volume group on this LVM)

The used dd command as follows:
dd if=/dev/loop0p2 of=/dev/sdb4 bs=8M status=progress

This finally made the files readable/attachable as a regular LVM in that partition space.

A resize was required to fill the partition as follows:
lvm pvresize -v /dev/sdb4

And then, lastly, I installed Grub Customizer which was able to detect the newly created LVM and add it to my on-system GRUB:
[ATTACH=CONFIG]269490[/ATTACH]

After this I can successfully boot into any of the 4 OS now on this system with the last one being correctly on it's original LVM setup.

=)

Thanks for your help and I hope this also helps any others in similar situations!

I shall mark this thread as solved.

---

