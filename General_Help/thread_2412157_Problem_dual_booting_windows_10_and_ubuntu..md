---
title: "Problem dual booting windows 10 and ubuntu."
date: 2019-02-08
forum: General Help
---

### Post by hirno93 on 2019-02-08
Ubuntu is currently booting fine, both ubuntu and windows 10 are showing up in the grub menu

Ubuntu is on the main hard drive of the computer and windows 10 is on a 128 GB usb stick on device /dev/sdb2
                 Boot Info Script 0.61      [1 April 2012]

```

============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 85 for .
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /tmp/BootInfo-eYMaCWqN/sdb1: unknown filesystem type ''.

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe

sdb3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /bootmgr /boot/bcd

ubuntu-vg-root': _______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /tmp/BootInfo-eYMaCWqN/sdb1: unknown filesystem type ''.
mount: /tmp/BootInfo-eYMaCWqN/LVM/ubuntu-vg-root': unknown filesystem type ''.

ubuntu-vg-swap_1': _____________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /tmp/BootInfo-eYMaCWqN/sdb1: unknown filesystem type ''.
mount: /tmp/BootInfo-eYMaCWqN/LVM/ubuntu-vg-root': unknown filesystem type ''.
mount: /tmp/BootInfo-eYMaCWqN/LVM/ubuntu-vg-swap_1': unknown filesystem type ''.

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 1,953,523,711 1,953,521,664  8e Linux LVM


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 119,3 GiB, 128043712512 bytes, 250085376 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sdb1 ends after the last sector of /dev/sdb

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048       264,191       262,144 Microsoft Reserved Partition (Windows)
/dev/sdb2         264,192   249,470,897   249,206,706 Data partition (Windows/Linux)
/dev/sdb3     249,470,898   250,085,336       614,439 EFI System partition

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop10                                             squashfs   
/dev/loop11                                             squashfs   
/dev/loop12                                             squashfs   
/dev/loop13                                             squashfs   
/dev/loop14                                             squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/loop8                                              squashfs   
/dev/loop9                                              squashfs   
/dev/mapper/ubuntu--vg-root bec42e06-a205-4022-9aac-3e1239b8649a   ext4       
/dev/mapper/ubuntu--vg-swap_1 3b95dabd-2278-4b81-b576-21170b01f2f8   swap       
/dev/sda1        YdTOcf-go2B-y2oX-MerW-WYTJ-UMeC-ErHlXx LVM2_member 
/dev/sdb1                                                          
/dev/sdb2        B470AC2970ABEFF2                       ntfs       win10
/dev/sdb3        9835-2039                              vfat       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
ubuntu--vg-root
ubuntu--vg-swap_1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/ubuntu--vg-root /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdb2        /media/simon/win10       fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb3

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 7e 0d  |.X.MSDOS5.0...~.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 b2 9f de 0e  |........?.......|
00000020  27 60 09 00 41 09 00 00  00 00 00 00 02 00 00 00  |'`..A...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 39 20 35 98 4e  4f 20 4e 41 4d 45 20 20  |..)9 5.NO NAME  |
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

Unknown BootLoader on ubuntu-vg-root'


Unknown BootLoader on ubuntu-vg-swap_1'



=============================== StdErr Messages: ===============================

  skip_dev_dir: Couldn't split up device name ubuntu-vg-root'.
  Volume group name "ubuntu-vg-root'" has invalid characters.
  Cannot process volume group ubuntu-vg-root'
  skip_dev_dir: Couldn't split up device name ubuntu-vg-root'.
  Volume group name "ubuntu-vg-root'" has invalid characters.
  Cannot process volume group ubuntu-vg-root'
  skip_dev_dir: Couldn't split up device name ubuntu-vg-root'.
  Volume group name "ubuntu-vg-root'" has invalid characters.
  Cannot process volume group ubuntu-vg-root'
hexdump: /dev/mapper/ubuntu-vg-root': No such file or directory
hexdump: /dev/mapper/ubuntu-vg-root': No such file or directory
  skip_dev_dir: Couldn't split up device name ubuntu-vg-swap_1'.
  Volume group name "ubuntu-vg-swap_1'" has invalid characters.
  Cannot process volume group ubuntu-vg-swap_1'
  skip_dev_dir: Couldn't split up device name ubuntu-vg-swap_1'.
  Volume group name "ubuntu-vg-swap_1'" has invalid characters.
  Cannot process volume group ubuntu-vg-swap_1'
  skip_dev_dir: Couldn't split up device name ubuntu-vg-swap_1'.
  Volume group name "ubuntu-vg-swap_1'" has invalid characters.
  Cannot process volume group ubuntu-vg-swap_1'
hexdump: /dev/mapper/ubuntu-vg-swap_1': No such file or directory
hexdump: /dev/mapper/ubuntu-vg-swap_1': No such file or directory
```

---

### Post by yancek on 2019-02-08
Your boot repair output is incomplete and does not show a lot of information which is generally shown.  Did you dowload it and burn it to a CD and boot it?  If you can boot Ubuntu, you might be better off going to the boot repair site at the link below and select the 2nd option.  Use the ppa and download it as it is more up to date.

Your windows has the EFI partition at the end of the drive which is a bit odd.  Has windows ever booted since you put it on the drive?  What software did you use to put it there as windows installer is designed to NOT install to a usb drive.  The standard message you would get is:     "windows setup does 
not support configuration or installation to a disk connected through usb or IEEE 1394 ports"

---

### Post by hirno93 on 2019-02-09
Ubuntu is booting fine, it's not boot repair ouput its from a script i ran after booting. Window has not booted. This is first boot. I used rufus to install windows on the go to the USB.

Did you mean to post a link to the ubuntu repair site or am i missing something? :) i'll gladly try it if you can provide the link to what you mean =)

---

### Post by yancek on 2019-02-09
> Did you mean to post a link to the ubuntu repair site

Yes I did and that's not the first and not likely the last time I forget to post a link.  Shown below, use the 2nd option explained on the page how to get it on your Ubuntu system to run.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Looking at your output from the initial post again, I see that the drive you have Ubuntu installed on is Legacy shown by "Disklabel type: dos" for /dev/sda while your windows drive is GPT with an EFI partition.  The Linux Grub bootloader installed in Legacy mode will not chainload boot an EFI install of windows.  So you would need to either convert Ubuntu to UEFI/GPT as explained at the site below or install it again in UEFI mode.  No guarantee this will work as putting windows on a usb has always been problematic by design with whatever software is used

  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

