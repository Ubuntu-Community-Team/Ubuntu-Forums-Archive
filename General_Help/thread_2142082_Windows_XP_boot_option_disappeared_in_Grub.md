---
title: "Windows XP boot option disappeared in Grub"
date: 2013-05-04
forum: General Help
---

### Post by giraflorens on 2013-05-04
I have two partitions in the hard drive.  One for Windows XP and the other for Ubuntu (v. 12.04)
Until now, when booting the Grub menu showed the Ubuntu and Windows options perfectly.
After restoring the Windows partition, the windows option has disappeared in the Grub Menu.

The Grub.lst file is not in /boot/grub folder and I tried update-grub.
The bootinfoscript results are below.
I would appreciate some help.


                 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /ntldr /NTDETECT.COM /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/swap.disk

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   915,333,119   915,331,072   7 NTFS / exFAT / HPFS
/dev/sda2         915,335,166   976,760,831    61,425,666   5 Extended
/dev/sda5         915,335,168   919,332,863     3,997,696  82 Linux swap / Solaris
/dev/sda6         919,334,912   958,394,367    39,059,456  83 Linux
/dev/sda7         958,396,416   976,760,831    18,364,416  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002  42 SFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        9228AEAD28AE8FB1                       ntfs       500GB
/dev/sda5        65c80dc9-120c-4112-b372-6c043509ffec   swap       
/dev/sda6        b2b93409-ad2f-474c-9d1b-f7a319e4a8ba   ext4       
/dev/sda7        2c39c5f4-ba1f-4d5f-9363-63d28eac5fbb   ext4       
/dev/sdb1        10C03EB4C03EA040                       ntfs       Disc Dos

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /home                    ext4       (rw)


=========================== sda6/boot/grub/grub.cfg: ===========================

---

### Post by oldfred on 2013-05-04
I am not sure if the grub in the MBR is correct or not. I have seen issues with the bootinfoscript report.

But you seem to have a wubi install in sda1 and two of three Windows boot files. Your sda1 does not have boot.ini. You then have a full install of Ubuntu in sda6. It that what you are booting? You have grub.cfg in sda6, but bootinfoscript did not show it?

You may have another Windows in sdb1, but it has been converted to dynamic partitioning. Linux cannot read dynamic partitions.

I would first try Boot-Repair. It also uses the Bootinfoscript as part of its BootInfo, but can also reinstall grub and make repairs.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

You may also want to convert sdb1 back to basic. 
      
 Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx]("http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx")

   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

---

### Post by giraflorens on 2013-05-04
Solved.  Thanks a lot.

Boot-Repair did the work all right!

---

