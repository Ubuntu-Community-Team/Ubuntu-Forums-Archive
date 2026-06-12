---
title: "Broken Grub (There are two of them)"
date: 2016-08-12
forum: General Help
---

### Post by lanetherif on 2016-08-12
Hi,

I've tried my luck in askubuntu to no avail. So here it comes:

Any ideas? 


I sort of botched the startup menu and boot partition. Now, I have two of them and none of them automatically loads (I have to choose Run Efi Application then choose the HDD).


Is there a possible way to revert to one boot partition?


Here is the result of bootinfoscript:




```
============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    55486016 of the same hard drive for core.img, but core.img can not be 
    found at this location.
 => No boot loader is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/fwupx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/MokManager.efi 
                       /efi/ubuntu/shimx64.efi


sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 55454200 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 16.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sda3: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sda4: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


sda5: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/MokManager.efi 
                       /efi/ubuntu/shimx64.efi


sdb2: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''


sdb3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe


sdb4: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________
Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       487,423       485,376 EFI System partition
/dev/sda2         487,424    78,612,479    78,125,056 Data partition (Linux)
/dev/sda3      78,612,480   102,049,791    23,437,312 Swap partition (Linux)
/dev/sda4     102,049,792 2,445,799,423 2,343,749,632 Data partition (Linux)
/dev/sda5   2,445,799,424 3,907,028,991 1,461,229,568 Data partition (Linux)


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT


/dev/sdb1 ends after the last sector of /dev/sdb


GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048       206,847       204,800 EFI System partition
/dev/sdb2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sdb3         468,992 1,952,602,111 1,952,133,120 Data partition (Windows/Linux)
/dev/sdb4   1,952,602,112 1,953,523,711       921,600 Windows Recovery Environment (Windows)


"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/sda1        A4C8-0534                              vfat       
/dev/sda2        77da29bf-6804-45c7-acbf-0b2161119498   ext4       
/dev/sda3        3bf35cd6-d20e-452b-864c-85f55497d420   swap       
/dev/sda4        9cb69512-d74d-490f-91ec-92e5225dc239   ext4       
/dev/sda5        83ef14f3-bf72-4a92-8681-ab6ee73d4620   ext4       
/dev/sdb1        1282-7C67                              vfat       
/dev/sdb2                                                          
/dev/sdb3        82F88AEEF88ADFB1                       ntfs       
/dev/sdb4        F056527156523914                       ntfs       


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sda2        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sda4        /home                    ext4       (rw,relatime,data=ordered)
/dev/sdb1        /boot/efi                vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)




=========================== sda2/boot/grub/grub.cfg: ===========================



```

---

### Post by yancek on 2016-08-12
Which windows version did you have installed, windows 7?  Was it an MBR or UEFI install?  Generally, a windows 7 system pre-installed would be MBR.  Some of the problems with your system include having and EFI partition on both hard drives which only contains the Ubuntu efi files.  Having Grub from Ubuntu installed in the MBR of sda.  If you use UEFI, you should not have boot code in the MBR but efi files in the EFI partition.  Note that there are no windows files in either EFI partition so if your machine is using UEFI, it won't boot windows.  

The bootinfoscript indicates you are using GPT on both hard drives.  My understanding is that if you use GPT with windows, you must use UEFI.  So is this windows 7, was it MBR, was it UEFI/GPT?

---

