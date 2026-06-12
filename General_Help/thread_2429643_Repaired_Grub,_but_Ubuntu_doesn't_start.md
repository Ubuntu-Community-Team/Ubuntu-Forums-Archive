---
title: "Repaired Grub, but Ubuntu doesn't start"
date: 2019-10-21
forum: General Help
---

### Post by giant-paw on 2019-10-21
Hi all, I'm newbie here and came after troubles began.

Recently my Windows 8.1 refused to start, and couldn't repair itself, in a Dual-Boot setting. I had tried to repair it with Live USB (Windows PE). Then this PE did something to the Grub. 2nd OS I have is Ubuntu 18 and it resulted in broken grub for both OSes.
Since then I've been trying to repair Grub.

I followed instructions from the 1st guy on [https://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd](https://askubuntu.com/questions/145241/how-do-i-run-update-grub-from-a-livecd) 
After this, Grub appeared with 4 options - Ubuntu, ubuntu recovery mode, memtest 1 and memetest 2. Purple colour, finally.
But when I lauch Ubuntu, it says that it's in emergency mode and doesn't proceed. I dunno why. But it gives me root access without any password. And says that sdb4 (read: sda4) is "fat FS, in read-only mode. error".
Maybe there's some way to make Ubuntu start normally again, or even write Windows option to Grub too?
For now, I only need Ubuntu working.
Here's some data in some files:
-------------
fstab entries:
# / was on /dev/sda1 during installation
uuid=<private>     /    ext4    errors=remount-ro 0   1
# /boot/efi was on /dev/sda3 during installation
uuid=<private.2> (short code)  /boot/efi      vfat       umask=0077    0     1
# /home was on /dev/sda2 during installation
uuid=<private.3>   /home         ext4    defaults          0          2
/swapfile                none    swap      sw         0            0
----------------------------
nano /etc/grub.d/10_linux   as follows:
#
prefix="/usr"
exec_prefix =/usr
datarootdir=usr/share
ubuntu_recovery=1
quiet-boot=1
quickboot=1
gfxpayload-dynamic=1
vt_handoff = 0   
-------------------
I changed  vt_handoff to 0,  was "1".
My BIOS runs in CSM mode.
If there was a scale of Ubuntu user knowledge from 1 to 10, I'd be on 2.
Hoping for your help.

---

### Post by Rubi1200 on 2019-10-21
Hi and welcome to the forums :-)

Best thing right now is to post the boot info summary (see first link in my signature).

Do not repair, just post summary here so we can take a closer look and offer advice on the best way to fix this.

Also, please post computer specifications especially RAM and graphics card.

Thanks.

---

### Post by giant-paw on 2019-10-21
I hope this is enough, but I have 2nd part just in case. In the end, I added recommendations of the program. I think they're quite useful.
CPU=Intel i5 1.8Ghz
RAM - 6Gb DDR3
NVidia/Intel Optimus (1 Gb)

```
 Boot Info Script 105643       [Boot-Info 10jun2017]


============================= Boot Info Summary: ===============================

 => No known boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 
    588044288 of the same hard drive for core.img. core.img is at this 
    location and looks for (,gpt1)/boot/grub. It also embeds following 
    components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda1: /dev/sda1 already mounted or mount point busy.

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 3747268. According to the info 
                       in the boot sector, sda2 has 0 sectors.
    Mounting failed:   mount: /mnt/BootInfo/sda1: /dev/sda1 already mounted or mount point busy.
mount: /mnt/BootInfo/sda2: /dev/sda2 already mounted or mount point busy.

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/i386-pc/core.img

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7/2008: FAT32
    Boot sector info:  According to the info in the boot sector, sdb4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb4 starts at sector 586043392.
    Mounting failed:   mount: /mnt/BootInfo/sda1: /dev/sda1 already mounted or mount point busy.
mount: /mnt/BootInfo/sda2: /dev/sda2 already mounted or mount point busy.
mount: /mnt/BootInfo/sdb4: can't read superblock on /dev/sdb4.

sdb5: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sdb6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda1: /dev/sda1 already mounted or mount point busy.
mount: /mnt/BootInfo/sda2: /dev/sda2 already mounted or mount point busy.
mount: /mnt/BootInfo/sdb4: can't read superblock on /dev/sdb4.
mount: /mnt/BootInfo/sdb6: unknown filesystem type ''.

sdb7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 1.9 GiB, 2026754538 bytes, 3948436 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *              0     3,805,135     3,815,236   0 Empty
/dev/sda2           3,747,268     3,741,859         4,672  ef EFI (FAT-12/16/32)

/dev/sda1 overlaps with /dev/sda2

GUID Partition Table detected, but does not seem to be used.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1   +  R              0     3,810,079     3,915,180 Data partition (Windows/Linux)
/dev/sda2   +  R      3,747,268     3,841,939         5,672 Data partition (Windows/Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 465.8 GiB, 500108862014 bytes, 976783167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdb1                 2,---    39-------1    39-------- Data partition (Linux)
/dev/sdb2            39,-------   39---------   35--------- Data partition (Linux)
/dev/sdb3           390,3-----2   5---------3   1---------2 Data partition (Windows/Linux)
/dev/sdb4           586,-------   58---------     2,------- EFI System partition
/dev/sdb5           588,-------   59--------3     2,0-----6 BIOS Boot partition
/dev/sdb6           590,0-----4   590-------7       2-----4 Microsoft Reserved Partition (Windows)
/dev/sdb7           590,3------   976,-------   38--------- Data partition (Windows/Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/sda1        numbers numbers num            iso9660    Ubuntu 18.04.1 LTS amd64
/dev/sda2        short-code:private                     vfat       
/dev/sdb1        Private                                ext4       
/dev/sdb2        Really, private                        ext4       
/dev/sdb3        same as before                         ntfs           0
/dev/sdb4        short code                             vfat       
/dev/sdb5                                                          
/dev/sdb6                                                          
/dev/sdb7        another code                           ntfs           0

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  4 Oct 16 18:06 ata-Slimtype_DVD_Not gonna see it!!!!!!!!!!!!!! -> ../../sr0
lrwxrwxrwx 1 root root  4 Oct 16 18:40 ata-WDC Really, Classified............ -> ../../sdb
lrwxrwxrwx 1 root root 10 Oct 16 18:40 ata-WDC_Classified-Classified-classified-classif -> ../../sdb1
lrwxrwxrwx 1 root root 10 Oct 16 18:40 ata-WDC_classified-classified-classified-classif-> ../../sdb2
lrwxrwxrwx 1 root root 10 Oct 16 18:40 ata-WDC_---------------------------------------- -> ../../sdb3
lrwxrwxrwx 1 root root 10 Oct 16 18:40 ata-WDC_---------------------------------------- -> ../../sdb4
lrwxrwxrwx 1 root root 10 Oct 16 18:40 ata-WDC_---------------------------------------- -> ../../sdb5
lrwxrwxrwx 1 root root 10 Oct 16 18:40 ata-WDC_---------------------------------------- -> ../../sdb6
lrwxrwxrwx 1 root root 10 Oct 16 18:40 ata-WDC_This app is quite Invasive. Top-Secret  -> ../../sdb7
lrwxrwxrwx 1 root root  9 Oct 16 18:40 usb-jesus......----------------------- -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 16 18:40 usb-------------------------------------part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 16 18:40 usb-------------------------------------part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Oct 16 18:40 wwn-xxxxxxxxxxxxxxxxxx -> ../../sdb
lrwxrwxrwx 1 root root 10 Oct 16 18:40 wwn-xxxxxxxxxxxxxxxxxx-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Oct 16 18:40 god save the queen..........-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Oct 16 18:40 wwn-xxxxxxxxxxxxxxxxxx-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 Oct 16 18:40 wwn-xxxxxxxxxxxxxxxxxx-part4 -> ../../sdb4
lrwxrwxrwx 1 root root 10 Oct 16 18:40 wwn-xxxxxxxxxxxxxxxxxx-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 Oct 16 18:40 wwn-xxxxxxxxxxxxxxxxxx-part6 -> ../../sdb6
lrwxrwxrwx 1 root root 10 Oct 16 18:40 xxxxgod Save Britain.......-part7 -> ../../sdb7

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda         /cdrom                   iso9660    (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)
/dev/sdb1        /media/ubuntu/Not gonna tell ya, omg               ext4       (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdb2        /media/ubuntu/Private                              ext4       (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)

=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to unsign) and reinstall the grub2 of sdb1 into the MBR of sdb.
Grub-efi would not be selected by default because: no-win-efi
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot


=================== Advice in case of suggested repair
Warning: continuing without internet would leave your system unbootable. Please connect internet.
EFI detected. You may want to retry after activating the [Separate /boot/efi partition:] option.
Do you want to continue?


=================== User settings
The settings chosen by the user will not act on the boot.





```

But I'm not eager to use Boot Repair. It uploads info about your computer *automatically, *very odd. "If this is a concern to you, don't use it" as they wrote. I hope there are more basic methods.

---

### Post by oldfred on 2019-10-21
There is not much, if any info that really says anything about your system, unless you label a partition with something that might be illegal.

But you seem to have Ubuntu installed in BIOS boot mode on a gpt partitioned drive that uses a bios_grub partition. That works for Ubuntu.
But Windows only boots from gpt with UEFI. Or only with BIOS from MBR partitioned drive.

If Windows was pre-installed, Microsoft required vendors to install in UEFI boot mode to gpt drives since 2012.
You seem to have part of a Windows install in sdb7, but that looks like a copy from some other location on drive. And it may be corrupt.

if not willing to post all the details and explain more about how you had Windows installed and then installed Ubuntu, we really cannot help. And then you best bet is just to totally reinstall everything & restore from your backups.

Just saw a Internet post that mentioned you do not have any important data unless you have it in three different places, at least one offsite.

---

### Post by giant-paw on 2019-10-22
Yes sorry for that, I'll give more info here. Windows had been pre-installed, but I deleted it and installed Ubuntu and fresh Windows 8.1. I wish I could remember which was the first. And yes Ubuntu has bios_grub partition.

I run the PC with external HDD, since it's taken out and there's no internal one. sdb1 is root, and sdb5 is probably bios_grub. There are 2 Windows partitions - sdb3, and sdb7 is OS.

Tell please any more info you need.

Maybe I can reinstall grub to MBR of sdb with some set of commands? And put Windows there too (optional).

---

### Post by oldfred on 2019-10-22
You have to decide if you want the now 35 year old BIOS boot or newer UEFI boot.
Since Windows was pre-installed it was UEFI and drive was gpt.

How you boot install media UEFI or BIOS is then how it installs for both Windows & Ubuntu.
In UEFI boot menu for flash drive you should have two boot options if Secure Boot is off.

If drive was gpt, and you did not reformat/repartition it, then Ubuntu could install in BIOS boot mode but would automatically add the bios_grub partition.
Windows then typically would only install in UEFI boot mode to gpt drive.  But it requires lots of extra partitions. See these for difference between UEFI & BIOS Windows standard installs:

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

If you want BIOS boot, you have to fully convert drive to MBR, so Windows will install. Windows requires a primary NTFS formatted partition with boot flag. You may have to reinstall grub as UUIDs will change.

If you want UEFI, then drive needs to be gpt partitioned. You can convert Ubuntu from BIOS boot to UEFI boot by adding an ESP - efi system partition and using Boot-Repair or manually totally reinstalling grub. Grub has two versions, one for BIOS, grub-pc and one for UEFI (64 bit PC) grub-efi-amd64. Then you should be able to reinstall or repair Windows.

Always boot installers & repair flash drives in the one mode you want, only UEFI or only BIOS.

---

