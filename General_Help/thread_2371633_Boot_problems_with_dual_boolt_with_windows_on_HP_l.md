---
title: "Boot problems with dual boolt with windows on HP laptop"
date: 2017-09-16
forum: General Help
---

### Post by tomsax on 2017-09-16
I'm having repeated problems installing ubuntu 16.04 on an HP Laptop.

It seemed to install okay and I was using it.

Then, when I shut computer down and tried to reboot I got to only a command line with this:

[I]BusyBox v1.22.1 (ubuntu1:1 .22.0 etc
(Initramfs)[/I]

I found a solution eventually by googling it.

Then this morning it failed again only going to the grub command line, with.

[I]Minimal BASH-like line editing is supported ....

grub>[/I]

I have tried the solution outlined in this website:

[https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/](https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/)

but, it just freezes each time when it gets to the boot repair.

So I am stumped.  

Love Ubuntu and have it on two other computers in the house but this one just can't seem to take it.  Very annoying.

If anybobdy knows how to fix that would be good.  I imagine that there are fixes but which wouldn't stop the problem reoccuring.  My previous tried solution to the above was to reinstall ubuntu again (have done that twice now).  

BTW Windows is booting okay when I choose that one.  But if I choose Ubuntu it goes to the above.

---

### Post by oldfred on 2017-09-16
UEFI or BIOS?
Is Windows working from grub or BIOS/UEFI directly?

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by tomsax on 2017-09-17
When I turn on laptop I have to press escape to get to the menu where I can go to boot options.  Otherwise it goes straight to Windows.  This is what I have had before on HP laptops.

Then I get to a (blueish) menu of options including windows, ubuntu and also "boot from EFI file" (or similar).
I choose Ubuntu and then I get to another (purplish) menu, which I think is the grub menu.  This also has the option of windows and ubuntu and boot repair (which didn't work) .  I choose Ubuntu and it goes straight to the grub command land but no further.  

Tom

---

### Post by tomsax on 2017-09-17
I'll try to create a boot summary report later when I have time. Thanks for your help so far.

---

### Post by tomsax on 2017-09-17
Here is the text file I got when I tried the Bootinfo summary.  It says something about pasting URL but that didn't appear.

```
 Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/fwupx64.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/mmx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       /EFI/HP/BIOSUpdate/CryptRSA.efi 
                       /EFI/HP/BIOSUpdate/CryptRSA32.efi 
                       /EFI/HP/BIOSUpdate/HpBiosMgmt.efi 
                       /EFI/HP/BIOSUpdate/HpBiosMgmt32.efi 
                       /EFI/HP/BIOSUpdate/HpBiosUpdate.efi 
                       /EFI/HP/BIOSUpdate/HpBiosUpdate32.efi 
                       /EFI/HP/SystemDiags/CryptRSA.efi 
                       /EFI/HP/SystemDiags/CryptRSA32.efi 
                       /EFI/HP/SystemDiags/HpSysDiags.efi 
                       /EFI/HP/SystemDiags/HpSysDiags32.efi 
                       /EFI/HP/SystemDiags/SystemDiags.efi 
                       /EFI/HP/SystemDiags/SystemDiags32.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: mount /dev/sda5 on /mnt/BootInfo/sda5 failed: Structure needs cleaning

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: mount /dev/sda5 on /mnt/BootInfo/sda5 failed: Structure needs cleaning
mount: /dev/sdb1 is already mounted or /mnt/BootInfo/sdb1 busy

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 3006684. According to the info 
                       in the boot sector, sdb2 has 0 sectors.
    Mounting failed:   mount: unknown filesystem type ''
mount: mount /dev/sda5 on /mnt/BootInfo/sda5 failed: Structure needs cleaning
mount: /dev/sdb1 is already mounted or /mnt/BootInfo/sdb1 busy
mount: /dev/sdb2 is already mounted or /mnt/BootInfo/sdb2 busy

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1                 2,048       534,527       532,480 EFI System partition
/dev/sda2               534,528       567,295        32,768 Microsoft Reserved Partition (Windows)
/dev/sda3               567,296 1,015,327,917 1,014,760,622 Data partition (Windows/Linux)
/dev/sda4      R  1,951,504,384 1,953,511,423     2,007,040 Windows Recovery Environment (Windows)
/dev/sda5         1,015,328,768 1,943,349,247   928,020,480 Data partition (Linux)
/dev/sda6         1,943,349,248 1,951,504,383     8,155,136 Swap partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 14.4 GiB, 15497953280 bytes, 30269440 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *              0     3,100,799     3,100,800   0 Empty
/dev/sdb2           3,006,684     3,011,355         4,672  ef EFI (FAT-12/16/32)

/dev/sdb1 overlaps with /dev/sdb2

GUID Partition Table detected, but does not seem to be used.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdb1   +  R              0     3,100,743     3,100,744 Data partition (Windows/Linux)
/dev/sdb2   +  R      3,006,684     3,011,355         4,672 Data partition (Windows/Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        30AF-A7C6                              vfat       SYSTEM
/dev/sda2                                                          
/dev/sda3        24DEB117DEB0E26A                       ntfs       WINDOWS
/dev/sda4        ACF0B1DAF0B1AACA                       ntfs       WINRE
/dev/sda5        dbb4436b-ad70-41ba-a2aa-860ba6703d8c   ext4       
/dev/sda6        3ec55c3b-0552-41a9-9471-c2f3671ed7e3   swap       
/dev/sdb1        2017-08-01-11-51-33-00                 iso9660    Ubuntu 16.04.3 LTS amd64
/dev/sdb2        398E-230F                              vfat       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Sep 17 11:17 ata-WDC_WD10JPVX-60JC3T1_WD-WXC1A57633AA -> ../../sda
lrwxrwxrwx 1 root root 10 Sep 17 11:17 ata-WDC_WD10JPVX-60JC3T1_WD-WXC1A57633AA-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Sep 17 11:17 ata-WDC_WD10JPVX-60JC3T1_WD-WXC1A57633AA-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Sep 17 11:18 ata-WDC_WD10JPVX-60JC3T1_WD-WXC1A57633AA-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Sep 17 11:18 ata-WDC_WD10JPVX-60JC3T1_WD-WXC1A57633AA-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Sep 17 11:17 ata-WDC_WD10JPVX-60JC3T1_WD-WXC1A57633AA-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Sep 17 11:17 ata-WDC_WD10JPVX-60JC3T1_WD-WXC1A57633AA-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 Sep 17 11:17 usb-Memorex_Mini_0703425A990AB702-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Sep 17 11:17 usb-Memorex_Mini_0703425A990AB702-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Sep 17 11:17 usb-Memorex_Mini_0703425A990AB702-0:0-part2 -> ../../sdb2
lrwxrwxrwx 1 root root  9 Sep 17 11:17 wwn-0x50014ee6079a80bc -> ../../sda
lrwxrwxrwx 1 root root 10 Sep 17 11:17 wwn-0x50014ee6079a80bc-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Sep 17 11:17 wwn-0x50014ee6079a80bc-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Sep 17 11:18 wwn-0x50014ee6079a80bc-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Sep 17 11:18 wwn-0x50014ee6079a80bc-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Sep 17 11:17 wwn-0x50014ee6079a80bc-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Sep 17 11:17 wwn-0x50014ee6079a80bc-part6 -> ../../sda6

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  78 ac 2d 00 00 00 00 00  15 cd 66 0d 00 00 80 00  |x.-.......f.....|
000001c0  01 00 00 5e e0 fb 00 00  00 00 80 50 2f 00 00 fe  |...^.......P/...|
000001d0  ff ff ef fe ff ff dc e0  2d 00 40 12 00 00 00 00  |........-.@.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


/dev/sdb1: unknown GPT attributes
1000000000000001

/dev/sdb2: unknown GPT attributes
1000000000000001
Unknown BootLoader on sdb1

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  78 ac 2d 00 00 00 00 00  15 cd 66 0d 00 00 80 00  |x.-.......f.....|
000001c0  01 00 00 5e e0 fb 00 00  00 00 80 50 2f 00 00 fe  |...^.......P/...|
000001d0  ff ff ef fe ff ff dc e0  2d 00 40 12 00 00 00 00  |........-.@.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/14786/mounts) leaked on lvs invocation. Parent PID 21816: bash
File descriptor 63 (pipe:[57036]) leaked on lvs invocation. Parent PID 21816: bash

ADDITIONAL INFORMATION :
=================== log of boot-info 2017-09-17__11h17 ===================
boot-info version : 4ppa40
boot-sav version : 4ppa40
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa40
grub-probe: error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
Warning: failed to translate partition name
Warning: The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.
Warning: failed to translate partition name
Warning: The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.
boot-info is executed in live-session (Ubuntu 16.04.3 LTS, xenial, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
ls: cannot access '/home/usr/.config': No such file or directory
mount: mount /dev/sda5 on /mnt/boot-sav/sda5 failed: Structure needs cleaning
mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: mount /dev/sda5 on /mnt/boot-sav/sda5 failed: Structure needs cleaning
mount -r /dev/sda5 : Error code 32
mount: /dev/sdb2 is already mounted or /mnt/boot-sav/sdb2 busy
mount /dev/sdb2 : Error code 32
mount -r /dev/sdb2 /mnt/boot-sav/sdb2
mount: /dev/sdb2 is already mounted or /mnt/boot-sav/sdb2 busy
mount -r /dev/sdb2 : Error code 32

=================== os-prober:
/dev/sda1@/efi/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
/dev/sda5:Ubuntu 16.04.3 LTS (16.04):Ubuntu:linux

=================== blkid:
/dev/sda1: LABEL="SYSTEM" UUID="30AF-A7C6" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="0e9891a5-dd40-4efb-8652-bf5e7e982a9f"
/dev/sda3: LABEL="WINDOWS" UUID="24DEB117DEB0E26A" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="4a428f3d-7577-4702-a401-1ac8dcda62e2"
/dev/sda4: LABEL="WINRE" UUID="ACF0B1DAF0B1AACA" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="fd87cb17-e2ea-46d3-aef0-e1095383e2b6"
/dev/sda5: UUID="dbb4436b-ad70-41ba-a2aa-860ba6703d8c" TYPE="ext4" PARTUUID="67a5594e-0fd3-4905-a798-cbf1f072dfc7"
/dev/loop0: TYPE="squashfs"
/dev/sda6: UUID="3ec55c3b-0552-41a9-9471-c2f3671ed7e3" TYPE="swap" PARTUUID="881e603b-7cf7-45fb-a935-5b894e4fa107"
/dev/sdb2: SEC_TYPE="msdos" UUID="398E-230F" TYPE="vfat" PARTUUID="0d66cd15-02"
/dev/sdb1: UUID="2017-08-01-11-51-33-00" LABEL="Ubuntu 16.04.3 LTS amd64" TYPE="iso9660" PTUUID="0d66cd15" PTTYPE="dos" PARTUUID="0d66cd15-01"
/dev/sda2: PARTLABEL="Microsoft reserved partition" PARTUUID="03574189-0b0d-4285-b785-3fc04ab776c2"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

mount: mount /dev/sda5 on /mnt/boot-sav/sda5 failed: Structure needs cleaning
mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: mount /dev/sda5 on /mnt/boot-sav/sda5 failed: Structure needs cleaning
mount -r /dev/sda5 : Error code 32
mount: /dev/sdb2 is already mounted or /mnt/boot-sav/sdb2 busy
mount /dev/sdb2 : Error code 32
mount -r /dev/sdb2 /mnt/boot-sav/sdb2
mount: /dev/sdb2 is already mounted or /mnt/boot-sav/sdb2 busy
mount -r /dev/sdb2 : Error code 32
Windows not detected by os-prober on sda3.
dd: invalid number: ‘0’
Warning: /var/log/boot-sav/log/2017-09-17__11h17boot-info41/sdb/current_mbr.img could not be created. Please report this message to boot.repair@gmail.com
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda1/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda1/EFI/Boot/bootx64.efi

=================== efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0001,3001,0002,2001,2002,2004
Boot0000* USB Hard Drive (UEFI) - Memorex Mini (Memorex Mini)	PciRoot(0x0)/Pci(0x10,0x0)/USB(5,0)/HD(1,MBR,0x21,0x2de0dc,0x1240)RC
Boot0001* Windows Boot Manager	HD(1,GPT,0e9891a5-dd40-4efb-8652-bf5e7e982a9f,0x800,0x82000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....+...............
Boot0002* ubuntu	HD(1,GPT,0e9891a5-dd40-4efb-8652-bf5e7e982a9f,0x800,0x82000)/File(EFIubuntushimx64.efi)
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot3001* Internal Hard Disk or Solid State Disk	RC

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda3	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda3.
sda4	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda4.
sda5	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda5.
sdb2	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdb2.

sda	: GPT,	no-BIOS_boot,	has-correctEFI, 	not-usb,	has-os,	2048 sectors * 512 bytes
sdb	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	usb-disk,	no-os,	0 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD10JPVX-60J (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system     Name                          Flags
1      1049kB  274MB   273MB   fat32           EFI system partition          boot, esp
2      274MB   290MB   16.8MB                  Microsoft reserved partition  msftres
3      290MB   520GB   520GB   ntfs            Basic data partition          msftdata
5      520GB   995GB   475GB   ext4
6      995GB   999GB   4175MB  linux-swap(v1)
4      999GB   1000GB  1028MB  ntfs                                          hidden, diag


Model: Memorex Mini (scsi)
Disk /dev/sdb: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:gpt:ATA WDC WD10JPVX-60J:;
1:1049kB:274MB:273MB:fat32:EFI system partition:boot, esp;
2:274MB:290MB:16.8MB::Microsoft reserved partition:msftres;
3:290MB:520GB:520GB:ntfs:Basic data partition:msftdata;
5:520GB:995GB:475GB:ext4::;
6:995GB:999GB:4175MB:linux-swap(v1)::;
4:999GB:1000GB:1028MB:ntfs::hidden, diag;

BYT;
/dev/sdb:15.5GB:scsi:512:512:unknown:Memorex Mini:;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sdb   disk iso9660   14.4G Ubuntu 16.04.3 LTS amd64
sdb2  part vfat       2.3M Ubuntu 16.04.3 LTS amd64
sdb1  part iso9660    1.5G Ubuntu 16.04.3 LTS amd64
loop0 loop squashfs   1.4G
sda   disk          931.5G
sda4  part ntfs       980M WINRE
sda2  part             16M
sda5  part ext4     442.5G
sda3  part ntfs     483.9G WINDOWS
sda1  part vfat       260M SYSTEM
sda6  part swap       3.9G

KNAME ROTA RO RM STATE   MOUNTPOINT
sdb      1  0  1 running /cdrom
sdb2     1  0  1
sdb1     1  0  1
loop0    1  1  0         /rofs
sda      1  0  0 running
sda4     1  0  0         /mnt/boot-sav/sda4
sda2     1  0  0
sda5     1  0  0
sda3     1  0  0         /mnt/boot-sav/sda3
sda1     1  0  0         /mnt/boot-sav/sda1
sda6     1  0  0         [SWAP]


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1947836k,nr_inodes=486959,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=399372k,mode=755)
/dev/sdb on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
aufs on / type aufs (rw,noatime,si=3cbe4de29d4e2a59)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=25,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=14189)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=399372k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 drm_dp_aux1 ecryptfs fb0 fd full fuse hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 initctl input kfd kmsg lightnvm log mapper mcelog media0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sdb sdb1 sdb2 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom userio v4l vfio vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 c6 a7 af 30 4e  4f 20 4e 41 4d 45 20 20  |..)...0NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 08 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  a8 04 7c 3c 00 00 00 00  |..........|<....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  6a e2 b0 de 17 b1 de 24  |........j......$|
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

=================== hexdump -n512 -C /dev/sda4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 98 51 74  |........?.....Qt|
00000020  00 00 00 00 80 00 80 00  ff 9f 1e 00 00 00 00 00  |................|
00000030  aa 46 01 00 00 00 00 00  02 00 00 00 00 00 00 00  |.F..............|
00000040  f6 00 00 00 01 00 00 00  ca aa b1 f0 da b1 f0 ac  |................|
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

=================== hexdump -n512 -C /dev/sdb2
00000000  eb 3c 90 6d 6b 66 73 2e  66 61 74 00 02 04 01 00  |.<.mkfs.fat.....|
00000010  02 00 02 40 12 f8 04 00  20 00 40 00 00 00 00 00  |...@.... .@.....|
00000020  00 00 00 00 80 00 29 0f  23 8e 39 4e 4f 20 4e 41  |......).#.9NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 32 20 20 20 0e 1f  |ME    FAT12   ..|
00000040  be 5b 7c ac 22 c0 74 0b  56 b4 0e bb 07 00 cd 10  |.[|.".t.V.......|
00000050  5e eb f0 32 e4 cd 16 cd  19 eb fe 54 68 69 73 20  |^..2.......This |
00000060  69 73 20 6e 6f 74 20 61  20 62 6f 6f 74 61 62 6c  |is not a bootabl|
00000070  65 20 64 69 73 6b 2e 20  20 50 6c 65 61 73 65 20  |e disk.  Please |
00000080  69 6e 73 65 72 74 20 61  20 62 6f 6f 74 61 62 6c  |insert a bootabl|
00000090  65 20 66 6c 6f 70 70 79  20 61 6e 64 0d 0a 70 72  |e floppy and..pr|
000000a0  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 74  |ess any key to t|
000000b0  72 79 20 61 67 61 69 6e  20 2e 2e 2e 20 0d 0a 00  |ry again ... ...|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs          tmpfs     391M  6.2M  384M   2% /run
/dev/sdb       iso9660   1.5G  1.5G     0 100% /cdrom
/dev/loop0     squashfs  1.5G  1.5G     0 100% /rofs
aufs           aufs      2.0G   71M  1.9G   4% /
tmpfs          tmpfs     2.0G  244K  2.0G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
tmpfs          tmpfs     2.0G   92K  2.0G   1% /tmp
tmpfs          tmpfs     391M   80K  390M   1% /run/user/999
/dev/sda1      vfat      256M   99M  158M  39% /mnt/boot-sav/sda1
/dev/sda3      fuseblk   484G   48G  437G  10% /mnt/boot-sav/sda3
/dev/sda4      fuseblk   980M  390M  591M  40% /mnt/boot-sav/sda4

=================== fdisk -l:
Disk /dev/loop0: 1.4 GiB, 1532116992 bytes, 2992416 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 15460A21-E9E3-44E5-B67C-3652EA7833A3

Device          Start        End    Sectors   Size Type
/dev/sda1        2048     534527     532480   260M EFI System
/dev/sda2      534528     567295      32768    16M Microsoft reserved
/dev/sda3      567296 1015327917 1014760622 483.9G Microsoft basic data
/dev/sda4  1951504384 1953511423    2007040   980M Windows recovery environment
/dev/sda5  1015328768 1943349247  928020480 442.5G Linux filesystem
/dev/sda6  1943349248 1951504383    8155136   3.9G Linux swap

Partition table entries are not in disk order.


Disk /dev/sdb: 14.4 GiB, 15497953280 bytes, 30269440 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0d66cd15

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdb1  *          0 3100799 3100800  1.5G  0 Empty
/dev/sdb2       3006684 3011355    4672  2.3M ef EFI (FAT-12/16/32)


No OS or WinEFI system
gui-tab-other.sh: line 93: _checkbutton_repairfilesystems: command not found


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems  fix-windows-boot


=================== User settings
The settings chosen by the user will not act on the boot.



```

---

### Post by oldfred on 2017-09-17
HP is not dual boot friendly. It violates UEFI spec that says NOT to use description as part of UEFI boot. And only valid description is "Windows Boot Manager".  But multiple work arounds depending on configuration.

I would first try with UEFI Secure Boot off.
Boot-Repair said it saw this:
> SecureBoot enabled.

Also do you have a proprietary video card/chip? If nVidia or AMD you need nomodeset.

With dual boot most find the fallback or hard drive entry will work.
You have a hard drive entry, but not sure if UEFI or BIOS boot.
Hard drive entry uses /EFI/Boot/bootx64.efi. You already have that file, but it probably is just a copy of Windows .efi boot file.
Boot-Repair will copy /EFI/ubuntu/shimx64.efi to be bootx64.efi and backup current entry. But Boot-Repair also sees all the HP .efi boot files in the ESP - efi system partition and adds a new 25_custom grub file with all those as grub menu entries.

So you can run Boot-Repair and it will automate the copy that these HP users did manually. But then may want to houseclean 25_custom. Or manually copy like these users had to do.
       HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 
    
Not sure if this is another error or from Secure Boot being on. 
      >  mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: mount /dev/sda5 on /mnt/boot-sav/sda5 failed: Structure needs cleaning 

    

So if Secure Boot off does not let you boot.
       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda5
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda5

---

### Post by tomsax on 2017-09-17
I've disabled Secure Boot.  

Tried to see if I had a AMD video card and it appears I have as I get 

```
ubuntu@ubuntu:~$ lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 98e4 (rev ea)
```

What does that mean I have to do?

Here is the Boot Info summary if that helps. Not sure what to do next.  Still have the same problem.

```

 Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => No known boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /dev/sda1 is already mounted or /mnt/BootInfo/sda1 busy

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 3006684. According to the info 
                       in the boot sector, sda2 has 0 sectors.
    Mounting failed:   mount: /dev/sda1 is already mounted or /mnt/BootInfo/sda1 busy
mount: /dev/sda2 is already mounted or /mnt/BootInfo/sda2 busy

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/fwupx64.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/mmx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       /EFI/HP/BIOSUpdate/CryptRSA.efi 
                       /EFI/HP/BIOSUpdate/CryptRSA32.efi 
                       /EFI/HP/BIOSUpdate/HpBiosMgmt.efi 
                       /EFI/HP/BIOSUpdate/HpBiosMgmt32.efi 
                       /EFI/HP/BIOSUpdate/HpBiosUpdate.efi 
                       /EFI/HP/BIOSUpdate/HpBiosUpdate32.efi 
                       /EFI/HP/SystemDiags/CryptRSA.efi 
                       /EFI/HP/SystemDiags/CryptRSA32.efi 
                       /EFI/HP/SystemDiags/HpSysDiags.efi 
                       /EFI/HP/SystemDiags/HpSysDiags32.efi 
                       /EFI/HP/SystemDiags/SystemDiags.efi 
                       /EFI/HP/SystemDiags/SystemDiags32.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /dev/sda1 is already mounted or /mnt/BootInfo/sda1 busy
mount: /dev/sda2 is already mounted or /mnt/BootInfo/sda2 busy
mount: unknown filesystem type ''

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe

sdb4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /dev/sda1 is already mounted or /mnt/BootInfo/sda1 busy
mount: /dev/sda2 is already mounted or /mnt/BootInfo/sda2 busy
mount: unknown filesystem type ''
mount: mount /dev/sdb5 on /mnt/BootInfo/sdb5 failed: Structure needs cleaning

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 14.4 GiB, 15497953280 bytes, 30269440 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *              0     3,100,799     3,100,800   0 Empty
/dev/sda2           3,006,684     3,011,355         4,672  ef EFI (FAT-12/16/32)

/dev/sda1 overlaps with /dev/sda2

GUID Partition Table detected, but does not seem to be used.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1   +  R              0     3,100,743     3,100,744 Data partition (Windows/Linux)
/dev/sda2   +  R      3,006,684     3,011,355         4,672 Data partition (Windows/Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdb1                 2,048       534,527       532,480 EFI System partition
/dev/sdb2               534,528       567,295        32,768 Microsoft Reserved Partition (Windows)
/dev/sdb3               567,296 1,015,327,917 1,014,760,622 Data partition (Windows/Linux)
/dev/sdb4      R  1,951,504,384 1,953,511,423     2,007,040 Windows Recovery Environment (Windows)
/dev/sdb5         1,015,328,768 1,943,349,247   928,020,480 Data partition (Linux)
/dev/sdb6         1,943,349,248 1,951,504,383     8,155,136 Swap partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2017-08-01-11-51-33-00                 iso9660    Ubuntu 16.04.3 LTS amd64
/dev/sda2        398E-230F                              vfat       
/dev/sdb1        30AF-A7C6                              vfat       SYSTEM
/dev/sdb2                                                          
/dev/sdb3        24DEB117DEB0E26A                       ntfs       WINDOWS
/dev/sdb4        ACF0B1DAF0B1AACA                       ntfs       WINRE
/dev/sdb5        dbb4436b-ad70-41ba-a2aa-860ba6703d8c   ext4       
/dev/sdb6        3ec55c3b-0552-41a9-9471-c2f3671ed7e3   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Sep 17 18:37 ata-WDC_WD10JPVX-60JC3T1_WD-WXC1A57633AA -> ../../sdb
lrwxrwxrwx 1 root root 10 Sep 17 18:37 ata-WDC_WD10JPVX-60JC3T1_WD-WXC1A57633AA-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Sep 17 18:37 ata-WDC_WD10JPVX-60JC3T1_WD-WXC1A57633AA-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Sep 17 18:38 ata-WDC_WD10JPVX-60JC3T1_WD-WXC1A57633AA-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 Sep 17 18:38 ata-WDC_WD10JPVX-60JC3T1_WD-WXC1A57633AA-part4 -> ../../sdb4
lrwxrwxrwx 1 root root 10 Sep 17 18:37 ata-WDC_WD10JPVX-60JC3T1_WD-WXC1A57633AA-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 Sep 17 18:37 ata-WDC_WD10JPVX-60JC3T1_WD-WXC1A57633AA-part6 -> ../../sdb6
lrwxrwxrwx 1 root root  9 Sep 17 18:37 usb-Memorex_Mini_0703425A990AB702-0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 Sep 17 18:37 usb-Memorex_Mini_0703425A990AB702-0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Sep 17 18:37 usb-Memorex_Mini_0703425A990AB702-0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Sep 17 18:37 wwn-0x50014ee6079a80bc -> ../../sdb
lrwxrwxrwx 1 root root 10 Sep 17 18:37 wwn-0x50014ee6079a80bc-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Sep 17 18:37 wwn-0x50014ee6079a80bc-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Sep 17 18:38 wwn-0x50014ee6079a80bc-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 Sep 17 18:38 wwn-0x50014ee6079a80bc-part4 -> ../../sdb4
lrwxrwxrwx 1 root root 10 Sep 17 18:37 wwn-0x50014ee6079a80bc-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 Sep 17 18:37 wwn-0x50014ee6079a80bc-part6 -> ../../sdb6

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sda

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  78 ac 2d 00 00 00 00 00  15 cd 66 0d 00 00 80 00  |x.-.......f.....|
000001c0  01 00 00 5e e0 fb 00 00  00 00 80 50 2f 00 00 fe  |...^.......P/...|
000001d0  ff ff ef fe ff ff dc e0  2d 00 40 12 00 00 00 00  |........-.@.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


/dev/sda1: unknown GPT attributes
1000000000000001

/dev/sda2: unknown GPT attributes
1000000000000001
Unknown BootLoader on sda1

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  78 ac 2d 00 00 00 00 00  15 cd 66 0d 00 00 80 00  |x.-.......f.....|
000001c0  01 00 00 5e e0 fb 00 00  00 00 80 50 2f 00 00 fe  |...^.......P/...|
000001d0  ff ff ef fe ff ff dc e0  2d 00 40 12 00 00 00 00  |........-.@.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/6595/mounts) leaked on lvs invocation. Parent PID 13664: bash
File descriptor 63 (pipe:[54092]) leaked on lvs invocation. Parent PID 13664: bash

ADDITIONAL INFORMATION :
=================== log of boot-info 2017-09-17__18h37 ===================
boot-info version : 4ppa40
boot-sav version : 4ppa40
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa40
grub-probe: error: cannot find a GRUB drive for /dev/sda1.  Check your device.map.
Warning: The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.
Warning: failed to translate partition name
Warning: The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.
Warning: failed to translate partition name
boot-info is executed in live-session (Ubuntu 16.04.3 LTS, xenial, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
ls: cannot access '/home/usr/.config': No such file or directory
mount: /dev/sda2 is already mounted or /mnt/boot-sav/sda2 busy
mount /dev/sda2 : Error code 32
mount -r /dev/sda2 /mnt/boot-sav/sda2
mount: /dev/sda2 is already mounted or /mnt/boot-sav/sda2 busy
mount -r /dev/sda2 : Error code 32
mount: mount /dev/sdb5 on /mnt/boot-sav/sdb5 failed: Structure needs cleaning
mount /dev/sdb5 : Error code 32
mount -r /dev/sdb5 /mnt/boot-sav/sdb5
mount: mount /dev/sdb5 on /mnt/boot-sav/sdb5 failed: Structure needs cleaning
mount -r /dev/sdb5 : Error code 32

=================== os-prober:
/dev/sdb1@/efi/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
/dev/sdb5:Ubuntu 16.04.3 LTS (16.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="2017-08-01-11-51-33-00" LABEL="Ubuntu 16.04.3 LTS amd64" TYPE="iso9660" PTUUID="0d66cd15" PTTYPE="dos" PARTUUID="0d66cd15-01"
/dev/sda2: SEC_TYPE="msdos" UUID="398E-230F" TYPE="vfat" PARTUUID="0d66cd15-02"
/dev/sdb1: LABEL="SYSTEM" UUID="30AF-A7C6" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="0e9891a5-dd40-4efb-8652-bf5e7e982a9f"
/dev/sdb3: LABEL="WINDOWS" UUID="24DEB117DEB0E26A" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="4a428f3d-7577-4702-a401-1ac8dcda62e2"
/dev/sdb4: LABEL="WINRE" UUID="ACF0B1DAF0B1AACA" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="fd87cb17-e2ea-46d3-aef0-e1095383e2b6"
/dev/sdb5: UUID="dbb4436b-ad70-41ba-a2aa-860ba6703d8c" TYPE="ext4" PARTUUID="67a5594e-0fd3-4905-a798-cbf1f072dfc7"
/dev/sdb6: UUID="3ec55c3b-0552-41a9-9471-c2f3671ed7e3" TYPE="swap" PARTUUID="881e603b-7cf7-45fb-a935-5b894e4fa107"
/dev/sdb2: PARTLABEL="Microsoft reserved partition" PARTUUID="03574189-0b0d-4285-b785-3fc04ab776c2"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

mount: /dev/sda2 is already mounted or /mnt/boot-sav/sda2 busy
mount /dev/sda2 : Error code 32
mount -r /dev/sda2 /mnt/boot-sav/sda2
mount: /dev/sda2 is already mounted or /mnt/boot-sav/sda2 busy
mount -r /dev/sda2 : Error code 32
mount: mount /dev/sdb5 on /mnt/boot-sav/sdb5 failed: Structure needs cleaning
mount /dev/sdb5 : Error code 32
mount -r /dev/sdb5 /mnt/boot-sav/sdb5
mount: mount /dev/sdb5 on /mnt/boot-sav/sdb5 failed: Structure needs cleaning
mount -r /dev/sdb5 : Error code 32
Windows not detected by os-prober on sdb3.
dd: invalid number: ‘0’
Warning: /var/log/boot-sav/log/2017-09-17__18h37boot-info42/sda/current_mbr.img could not be created. Please report this message to boot.repair@gmail.com
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sdb1/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sdb1/EFI/Boot/bootx64.efi

=================== efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0001,3001,0002,2001,2002,2004
Boot0000* USB Hard Drive (UEFI) - Memorex Mini (Memorex Mini)	PciRoot(0x0)/Pci(0x10,0x0)/USB(6,0)/HD(1,MBR,0x21,0x2de0dc,0x1240)RC
Boot0001* Windows Boot Manager	HD(1,GPT,0e9891a5-dd40-4efb-8652-bf5e7e982a9f,0x800,0x82000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....+...............
Boot0002* ubuntu	HD(1,GPT,0e9891a5-dd40-4efb-8652-bf5e7e982a9f,0x800,0x82000)/File(EFIubuntushimx64.efi)
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot3001* Internal Hard Disk or Solid State Disk	RC

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)


=================== PARTITIONS & DISKS:
sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda2.
sdb1	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdb1.
sdb3	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb3.
sdb4	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb4.
sdb5	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb5.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	usb-disk,	no-os,	0 sectors * 512 bytes
sdb	: GPT,	no-BIOS_boot,	has-correctEFI, 	not-usb,	has-os,	2048 sectors * 512 bytes


=================== parted -l:

Model: Memorex Mini (scsi)
Disk /dev/sda: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

Model: ATA WDC WD10JPVX-60J (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system     Name                          Flags
1      1049kB  274MB   273MB   fat32           EFI system partition          boot, esp
2      274MB   290MB   16.8MB                  Microsoft reserved partition  msftres
3      290MB   520GB   520GB   ntfs            Basic data partition          msftdata
5      520GB   995GB   475GB   ext4
6      995GB   999GB   4175MB  linux-swap(v1)
4      999GB   1000GB  1028MB  ntfs                                          hidden, diag

=================== parted -lm:

BYT;
/dev/sda:15.5GB:scsi:512:512:unknown:Memorex Mini:;

BYT;
/dev/sdb:1000GB:scsi:512:4096:gpt:ATA WDC WD10JPVX-60J:;
1:1049kB:274MB:273MB:fat32:EFI system partition:boot, esp;
2:274MB:290MB:16.8MB::Microsoft reserved partition:msftres;
3:290MB:520GB:520GB:ntfs:Basic data partition:msftdata;
5:520GB:995GB:475GB:ext4::;
6:995GB:999GB:4175MB:linux-swap(v1)::;
4:999GB:1000GB:1028MB:ntfs::hidden, diag;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sdb   disk          931.5G
sdb4  part ntfs       980M WINRE
sdb2  part             16M
sdb5  part ext4     442.5G
sdb3  part ntfs     483.9G WINDOWS
sdb1  part vfat       260M SYSTEM
sdb6  part swap       3.9G
loop0 loop squashfs   1.4G
sda   disk iso9660   14.4G Ubuntu 16.04.3 LTS amd64
sda2  part vfat       2.3M Ubuntu 16.04.3 LTS amd64
sda1  part iso9660    1.5G Ubuntu 16.04.3 LTS amd64

KNAME ROTA RO RM STATE   MOUNTPOINT
sdb      1  0  0 running
sdb4     1  0  0         /mnt/boot-sav/sdb4
sdb2     1  0  0
sdb5     1  0  0
sdb3     1  0  0         /mnt/boot-sav/sdb3
sdb1     1  0  0         /mnt/boot-sav/sdb1
sdb6     1  0  0         [SWAP]
loop0    1  1  0         /rofs
sda      1  0  1 running /cdrom
sda2     1  0  1
sda1     1  0  1


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1947868k,nr_inodes=486967,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=399380k,mode=755)
/dev/sda on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
aufs on / type aufs (rw,noatime,si=aa55131a97772467)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=24,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=14738)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=399380k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sdb1 on /mnt/boot-sav/sdb1 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb3 on /mnt/boot-sav/sdb3 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb4 on /mnt/boot-sav/sdb4 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdb1 sdb2 sdb3 sdb4 sdb5 sdb6 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 drm_dp_aux1 ecryptfs fb0 fd full fuse hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 initctl input kfd kmsg lightnvm log mapper mcelog media0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sdb sdb1 sdb2 sdb3 sdb4 sdb5 sdb6 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom userio v4l vfio vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda2
00000000  eb 3c 90 6d 6b 66 73 2e  66 61 74 00 02 04 01 00  |.<.mkfs.fat.....|
00000010  02 00 02 40 12 f8 04 00  20 00 40 00 00 00 00 00  |...@.... .@.....|
00000020  00 00 00 00 80 00 29 0f  23 8e 39 4e 4f 20 4e 41  |......).#.9NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 32 20 20 20 0e 1f  |ME    FAT12   ..|
00000040  be 5b 7c ac 22 c0 74 0b  56 b4 0e bb 07 00 cd 10  |.[|.".t.V.......|
00000050  5e eb f0 32 e4 cd 16 cd  19 eb fe 54 68 69 73 20  |^..2.......This |
00000060  69 73 20 6e 6f 74 20 61  20 62 6f 6f 74 61 62 6c  |is not a bootabl|
00000070  65 20 64 69 73 6b 2e 20  20 50 6c 65 61 73 65 20  |e disk.  Please |
00000080  69 6e 73 65 72 74 20 61  20 62 6f 6f 74 61 62 6c  |insert a bootabl|
00000090  65 20 66 6c 6f 70 70 79  20 61 6e 64 0d 0a 70 72  |e floppy and..pr|
000000a0  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 74  |ess any key to t|
000000b0  72 79 20 61 67 61 69 6e  20 2e 2e 2e 20 0d 0a 00  |ry again ... ...|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 c6 a7 af 30 4e  4f 20 4e 41 4d 45 20 20  |..)...0NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 08 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  a8 04 7c 3c 00 00 00 00  |..........|<....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  6a e2 b0 de 17 b1 de 24  |........j......$|
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

=================== hexdump -n512 -C /dev/sdb4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 98 51 74  |........?.....Qt|
00000020  00 00 00 00 80 00 80 00  ff 9f 1e 00 00 00 00 00  |................|
00000030  aa 46 01 00 00 00 00 00  02 00 00 00 00 00 00 00  |.F..............|
00000040  f6 00 00 00 01 00 00 00  ca aa b1 f0 da b1 f0 ac  |................|
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

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs          tmpfs     391M  6.3M  384M   2% /run
/dev/sda       iso9660   1.5G  1.5G     0 100% /cdrom
/dev/loop0     squashfs  1.5G  1.5G     0 100% /rofs
aufs           aufs      2.0G  106M  1.9G   6% /
tmpfs          tmpfs     2.0G  404K  2.0G   1% /dev/shm
tmpfs          tmpfs     5.0M  8.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
tmpfs          tmpfs     2.0G   32K  2.0G   1% /tmp
tmpfs          tmpfs     391M   80K  390M   1% /run/user/999
/dev/sdb1      vfat      256M  102M  155M  40% /mnt/boot-sav/sdb1
/dev/sdb3      fuseblk   484G   48G  437G  10% /mnt/boot-sav/sdb3
/dev/sdb4      fuseblk   980M  390M  591M  40% /mnt/boot-sav/sdb4

=================== fdisk -l:
Disk /dev/loop0: 1.4 GiB, 1532116992 bytes, 2992416 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 14.4 GiB, 15497953280 bytes, 30269440 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0d66cd15

Device     Boot   Start     End Sectors  Size Id Type
/dev/sda1  *          0 3100799 3100800  1.5G  0 Empty
/dev/sda2       3006684 3011355    4672  2.3M ef EFI (FAT-12/16/32)


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 15460A21-E9E3-44E5-B67C-3652EA7833A3

Device          Start        End    Sectors   Size Type
/dev/sdb1        2048     534527     532480   260M EFI System
/dev/sdb2      534528     567295      32768    16M Microsoft reserved
/dev/sdb3      567296 1015327917 1014760622 483.9G Microsoft basic data
/dev/sdb4  1951504384 1953511423    2007040   980M Windows recovery environment
/dev/sdb5  1015328768 1943349247  928020480 442.5G Linux filesystem
/dev/sdb6  1943349248 1951504383    8155136   3.9G Linux swap

Partition table entries are not in disk order.


No OS or WinEFI system
gui-tab-other.sh: line 93: _checkbutton_repairfilesystems: command not found


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems  fix-windows-boot


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2017-09-17
When you get to grub menu, which may need pressing escape during UEFI boot before grub normally should appear, add nomodeset.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

I do not know AMD and which driver works. It has an open source driver that often works without the nomodeset.

       
 Radeon: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
AMDGPU: [https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)
AMDGPU-PRO: [https://help.ubuntu.com/community/AMDGPU-PRO-Driver](https://help.ubuntu.com/community/AMDGPU-PRO-Driver)

---

### Post by tomsax on 2017-09-17
I've tried to put to nomodeset but I can only do it going into grub with the ubuntu recovery flashdrive, then when I boot up from that it is fine but that is fine anyway without this change.
If I try and boot from the internal drive it is still the same.

I realise my description of how I get to the grub command line above seems to be wrong:  I need to press escape not to go straight to windows and doing so I get a blue menu, one of which is F9 boot options. I then get to another menu which refers to the BIOS  It has the options for windows and ubuntu. It is called Boot manager I think. If I have the recovery flash drive that is available too.  

If I choose ubuntu I just go to the grub command line but no options and e for edit doesn't work. 

So i don't have the grub menu to press e for edit.

Tried to do it from the recovery disc using the option to change to nomodeset permanantly but that doesn't work either.

I tired boot repair again from the recovery flash drive but it just freezes during the repair and stops.

Will try again tomorrow.

---

### Post by oldfred on 2017-09-17
I thought those with HP could boot one time (each time) using UEFI boot menu. It was just that you could not set the UEFI ubuntu entry to default for first in boot order. Or when you do it resets on next boot.
But can you boot the hard drive entry after you manually copy shimx64.efi to bootx64.efi as per threads posted above. Also instructions in link below in my signature. See A. in section on systems that only boot Windows.

---

### Post by tomsax on 2017-09-18
I decided to start from scratch again and reloaded Windows and then Ubuntu for dual boot.  I disabled Secure Boot.  This time I connected to the internet via a cable which seems to make for a smoother install.  It now goes to gnu grub when I boot up and goes straight into Ubuntu when I request it.  I don't have to press ESC on booting up.

But, after 5 minutes it has now frozen with no response from the keyboard or mouse.  

If it goes like before it  will soon fail to load Ubuntu when asked and go straight to grub command land.

But perhaps not.  Will write as solved if can solve the screen frozen issue as I suspect it is related.

Tom

---

### Post by oldfred on 2017-09-18
That may be related to video driver. 
Have you installed correct video driver for your AMD card/chip?
Sometimes proprietary driver is required as open source one is not quite as up to date.

---

### Post by tomsax on 2017-09-19
After turning off after freezing yesterday I am back to the same problem.  I don't get the grub menu now as it goes straight to Windows.  If I press escape on start up I can then get to the following;
[ATTACH=CONFIG]276778[/ATTACH]

I choose ubuntu and then get this:

[ATTACH=CONFIG]276779[/ATTACH]

So I can't edit the grub to make video card nomodeset on the way in.

I tried using the ubuntu flash drive to use ubuntu temporarily to then edit to nomodeset but I think that is only a temporary change.  When I restart I get the same issue again.

Not sure how I can install correct right video driver from here.  Do I need to reinstall ubuntu to try and get back to how I was last night before it froze and got corrupted again?  Or is there another way?

I read all the other threads but I do not know what is applicable to my case.  I did a reinstall of windows and ubuntu before  as I had made lots of changes which had no apparent effect but I wasn't sure if I was actually making things worse.

---

### Post by oldfred on 2017-09-19
You are seeing UEFI boot menu and then you have a grub error of some sort.
Often easiest to to reinstall grub.
Did you install both Windows and Ubuntu in UEFI boot mode? How you boot install media is then how it installs.
You may be then booting Ubuntu in wrong boot mode.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by tomsax on 2017-09-21
I tried to reload windows and ubuntu booting directly from the drivers and that failed on ubuntu installation, so all corrupted.  Was hoping to get to the grub and edit to nomodeset before I lost it again.  I can't even get to finish an ubuntu installation now.

[https://ubuntuforums.org/showthread.php?t=2372122&p=13689270#post13689270](https://ubuntuforums.org/showthread.php?t=2372122&p=13689270#post13689270)

---

### Post by tomsax on 2017-09-23
I managed to put Ubuntu back on the laptop.  I also managed to reboot and add nomodeset. I had disabled Secure boot and Legacy boot.  So far I have not had problems but I have not rebooted yet.  I'm going to suspend only until I get a reply to this as I am worried it could all go wrong again if I don't make some more changes.  

I still have to press Esc on start up, go to boot options, choose ubuntu and then choose ubuntu again in grub,, but I think that this is just how it has to be on an HP computer.

I am just worried that it might freeze again or that it might not install from grub (as before) if I reboot.

---

### Post by oldfred on 2017-09-23
HP will reset UEFI to boot Windows.
And it violated UEFI standard that says NOT to use description & on valid description is "Windows Boot Manager", but multiple work arounds.

Boot-Repair will copy shimx64.efi to /EFI/Boot/bootx64.efi which is a fallback or hard drive boot entry. Many HPs have that entry but bootx64.efi is just  a copy of Windows .efi boot file.
Before Boot-Repair copied file, users had to manually copy file.

       HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

Also details in link in my signature.
       
 Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

### Post by efflandt on 2017-09-23
It looks like something may have corrupted your Linux partition, because in the first Boot-Info report showed this:

```
sda5: __________________________________________________________________________ 
    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: mount /dev/sda5 on /mnt/BootInfo/sda5 failed: Structure needs cleaning
```Make sure that you have "Fast Boot" **disabled** in Windows. That is a form of hibernation which marks partitions as dirty, so they will not be mounted.

From live/install system try running the following and see if it can find/fix whatever errors. Normally Ubuntu would automatically try to fix that with e2fsck -p option, but maybe it cannot fix it automatically:```
sudo e2fsck /dev/sda5
```

I have a low end HP Win10 laptop, but it has a Pentium CPU with integrated graphics (slow). Other than having to hit Esc while booting, then F9 to select ubuntu, it works fine.

---

### Post by johndough2 on 2017-09-24
Hi

[ATTACH=CONFIG]276829[/ATTACH]

I have made my boot order opensuse, Windows and lastly zzzDebian.

If left to HP it would be in alphabetical order, and depending on whether it's called MS or Windows affects the sequence.

MS will be preferred to Ubuntu, but Windows will defer to Ubuntu.

---

### Post by tomsax on 2017-09-24
It is still working so that's great.  I''ll mark this thread as solved.

Thanks very much for your help oldfred.  I couldn't have sorted without that

I remember now I did disable Fastboot after reading that recommendation somewhere.

---

