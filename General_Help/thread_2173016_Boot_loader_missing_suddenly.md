---
title: "Boot loader missing suddenly"
date: 2013-09-07
forum: General Help
---

### Post by neela on 2013-09-07
This morning I find that my bootloader is missing.
I tried to use boot-repair, but it did not work. Wanted me to create a small boot partition. I already have two partitions with the bios-grub flag turned on -- not sure what I am missing.
Here is the link with the bootinfo summary.

[http://paste.ubuntu.com/6075859](http://paste.ubuntu.com/6075859)
Would appreciate any help.

Thank you.

---

### Post by ajgreeny on 2013-09-07
A few things to say which may help.
[LIST=1]
[*]Has the OS ever booted or has this problem just appeared? 
[*]You have a BIOS boot partition which I do not have, in fact you have two of them, and I thought they were only needed in other circumstances to yours when dual booting, though I am no expert and have not dual booted with windows for a few years, only with other Linux distros. 
[*]You appear to have UEFI system and GPT partitions but there is no EFI partition that I can see which may be an ommision. 
[*]I note that secure boot is enabled.  As you are not running a windows dual boot there is no point in having that enabled so I suggest you disable it by going to the UEFI setup.  Look for how to do that just after powering on, usually "Press Del or F# to enter setup" 
[*]There is no grub installed at all as far as I can see but you have syslinux installed in the MBR of sda.  I have no idea if that is a problem, but on my system with Xubuntu 12.04.3 64bit, on a UEFI system I have a very different partition and setup to yours.  See the first few stanzas of my bootinfoscript RESULTS.txt file below, and compare it with yours. 
[*]Read and try to understand [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") if you have not already done so; it may give you just the info you need to solve this. 
[/LIST]

Here's my RESULTS.txt for comparison.
```
============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf

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

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       411,647       409,600 EFI System partition
/dev/sda2         411,648    41,371,647    40,960,000 Data partition (Windows/Linux)
/dev/sda3   1,936,732,160 1,953,523,711    16,791,552 Swap partition (Linux)
/dev/sda4      41,371,648 1,936,732,159 1,895,360,512 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        B8F6-7B31                              vfat       
/dev/sda2        1fd42bfe-b5d4-4389-9607-1207af1c3e8b   ext4       Xubuntu
/dev/sda3        0707fdc8-1299-4c11-9f93-8158d3c313d0   swap       
/dev/sda4        2a1a9b57-4d0a-4570-974f-d6114fb25ef1   ext4       Home

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat       (rw)
/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda4        /home                    ext4       (rw)


```
The lines 384 to 939 of your bootinfoscript file seem to confirm the suggestions my above suspicion.
```

(debug) reinstall grub2 place-in-MBR no-BIOS_boot (sdb2)
=================== Repair blocked
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
(debug) reinstall grub2 place-in-MBR no-BIOS_boot (sdb2)
=================== Repair blockers
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
=================== Advice displayed in case of recommended repair
[COLOR=#ff0000]The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB~250MB, start of the disk, boot flag).
Do you want to continue?The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB~250MB, start of the disk, boot flag).
Do you want to continue?[/COLOR]
```You may wish to carry out the suggested repair, though I am uncertain whether boot-repair can make the new partition itself or if you need to do that yourself first.

---

### Post by oldfred on 2013-09-08
The suggestion by Boot-Repair for a bios_grub partition is to convert your install to BIOS booting from UEFI booting. But you do show an efi partition sda1. It is fat32 and has boot flag showing it as the efi partition. Not sure if error on partition start is the issue or your sda1 has some other issue but it seems both UEFI and Boot-Repair cannot read the data in the partition.

Can you mount and copy the efi folders in the efi partiition from your live installer that you ran Boot0-Repair from? If so I might fully backup efi partition, and using gparted just delete partition, and recreate it as same size, same format fat32, add boot flag with manage flags and copy efi folder(s) back into it.
You may be able to run repairs on the partition.
This might work.
 sudo /sbin/fsck.vfat -V /dev/sda1

---

