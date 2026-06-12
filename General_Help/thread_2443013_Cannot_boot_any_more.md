---
title: "Cannot boot any more"
date: 2020-05-10
forum: General Help
---

### Post by monkeybrain20122 on 2020-05-10
I have accidentally messed up the boot partition in my Ubuntu 20.04. When boot it says it is not a boot disk please insert a bootable floppy (??!!) and press any key .. My boot partition is empty at this point. boot-repair didn't fix it and here is the output
[https://paste.ubuntu.com/p/Cx8b35nqc3/](https://paste.ubuntu.com/p/Cx8b35nqc3/)

```

boot-repair-4ppa107                                              [20200510_1113]

============================= Boot Repair Summary ==============================



Warning: The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.
Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will restore the [(generic mbr)] MBR in sda, and make it boot on sda1.
Additional repair will be performed: unhide-bootmenu-10s


sdb2 is 100 % full
The sdb2 (Linux) partition is still full. This can prevent to start it (e.g. you may get a Power Manager error).

============================== Restore MBR of sda ==============================

dd if=/usr/lib/syslinux/mbr/mbr.bin of=/dev/sda

Boot successfully repaired.

You can now reboot your computer.


============================ Boot Info After Repair ============================

 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sda.
 => Windows 7/8/2012 is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04 LTS 
    Boot files:        /etc/fstab /etc/default/grub

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sdb: /dev/sdb already mounted or mount point busy.


================================ 5 OS detected =================================

OS#1:   Ubuntu 20.04 LTS on sda5
OS#2:   Linux on sda1
OS#3:   Linux on sdb2
OS#4:   Linux on sdb3
OS#5:   Linux on sdc1

============================ Architecture/Host Info ============================

CPU architecture: 64-bit
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04 LTS, focal, x86_64)

===================================== UEFI =====================================

This live-session is not in EFI-mode.

f7a57b08bc7c1c85417ae4cea582d1d4   sdb2/boot/bootx64.efi
109e2fc4aa9786cd887ed6f95c485951   sdb2/boot/grubx64.efi
4487628005555bfd4a4c0a47211e0700   sdb2/boot/mmx64.efi


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : notGPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes
sdb    : notGPT,    no-BIOSboot,    has---ESP,     usb-disk,    not-mmc, has-os,    0 sectors * 512 bytes
sdc    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : is-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda5    : is-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdb2    : is-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdb3    : is-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdc1    : is-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

sda1    : is---ESP,    part-has-no-fstab,    notbiosboot,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda5    : isnotESP,    fstab-has-goodEFI,    notbiosboot,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb2    : is---ESP,    part-has-no-fstab,    notbiosboot,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb3    : isnotESP,    part-has-no-fstab,    notbiosboot,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc1    : isnotESP,    part-has-no-fstab,    notbiosboot,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda5    : not-sepboot,    no-boot,    fstab-without-boot,    not-sep-usr,    no---usr,    fstab-without-usr,    std-grub.d,    sda
sdb2    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sdb
sdb3    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sdb
sdc1    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sdc

fdisk -l (filtered): ___________________________________________________________

Disk sda: 238.49 GiB, 256060514304 bytes, 500118192 sectors
Disk identifier: 0xe1f946f3
      Boot   Start       End   Sectors  Size Id Type
sda1  *       2048   1050623   1048576  512M  b W95 FAT32
sda2       1052670 500117503 499064834  238G  5 Extended
sda5       1052672 500117503 499064832  238G 83 Linux
Disk sdb: 7.47 GiB, 8006074368 bytes, 15636864 sectors
Disk identifier: 0x15f006ae
      Boot   Start      End  Sectors  Size Id Type
sdb1  *          0  5303231  5303232  2.5G  0 Empty
sdb2       4222640  4230575     7936  3.9M ef EFI (FAT-12/16/32)
sdb3       5304320 15636863 10332544  4.9G 83 Linux
Disk sdc: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 0xafcff92c
      Boot Start        End    Sectors   Size Id Type
sdc1  *     2048 1953521663 1953519616 931.5G 83 Linux

parted -lm (filtered): _________________________________________________________

sda:256GB:scsi:512:512:msdos:ATA TOSHIBA THNSNS25:;
1:1049kB:538MB:537MB:fat32::boot;
2:539MB:256GB:256GB:::;
5:539MB:256GB:256GB:ext4::;
sdb:8006MB:scsi:512:512:unknown:Kingston DT 101 G2:;
sdc:1000GB:scsi:512:4096:msdos:ADATA HD650:;
1:1049kB:1000GB:1000GB:ext4::boot;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda                                                                                                              
â&#8221;&#339;â&#8221;&#8364;sda1 vfat     CEDA-F9ED                            e1f946f3-01                                                 
â&#8221;&#339;â&#8221;&#8364;sda2                                               e1f946f3-02                                                 
â&#8221;&#8221;â&#8221;&#8364;sda5 ext4     a63cc7f9-6d36-4bc9-bd22-2ab964e81bb5 e1f946f3-05                                                 
sdb    iso9660  2020-04-23-07-51-42-00                                                    Ubuntu 20.04 LTS amd64 
â&#8221;&#339;â&#8221;&#8364;sdb1 iso9660  2020-04-23-07-51-42-00               15f006ae-01                          Ubuntu 20.04 LTS amd64 
â&#8221;&#339;â&#8221;&#8364;sdb2 vfat     1AC3-20ED                            15f006ae-02                                                 
â&#8221;&#8221;â&#8221;&#8364;sdb3 ext4     114de909-5f04-43b9-85a3-9e95e64fe226 15f006ae-03                          writable               
sdc                                                                                                              
â&#8221;&#8221;â&#8221;&#8364;sdc1 ext4     34d8202f-688d-4076-b3b6-f8a0e99dc4a8 afcff92c-01                          bkup                   

df (filtered): _________________________________________________________________

                                                          Avail Use% Mounted on
disk/by-label/writable[/install-logs-2020-05-10.5/crash]   4.5G   1% /var/crash
disk/by-label/writable[/install-logs-2020-05-10.5/log]     4.5G   1% /var/log
sda1                                                       511M   0% /mnt/boot-sav/sda1
sda5                                                     179.7G  18% /media/ubuntu/a63cc7f9-6d36-4bc9-bd22-2ab964e81bb5
sdb1                                                          0 100% /cdrom
sdb2                                                        10K 100% /mnt/boot-sav/sdb2
sdc1                                                     695.7G  19% /media/ubuntu/bkup

Mount options: __________________________________________________________________

disk/by-label/writable[/install-logs-2020-05-10.5/crash] rw,relatime
disk/by-label/writable[/install-logs-2020-05-10.5/log]   rw,relatime
sda1                                                     rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
sda5                                                     rw,nosuid,nodev,relatime
sdb1                                                     ro,noatime,nojoliet,check=s,map=n,blocksize=2048
sdb2                                                     rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
sdc1                                                     rw,nosuid,nodev,relatime,stripe=8191

========================== sda5/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=a63cc7f9-6d36-4bc9-bd22-2ab964e81bb5 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=CEDA-F9ED  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

======================= sda5/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
#GRUB_TERMINAL=console
#GRUB_GFXMODE=640x480
#GRUB_DISABLE_LINUX_UUID=true
#GRUB_DISABLE_RECOVERY="true"
#GRUB_INIT_TUNE="480 440 1"


======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown BootLoader on sda2

00000000  38 64 38 66 39 62 36 36  37 22 2c 22 61 70 70 6c  |8d8f9b667","appl|
00000010  69 63 61 74 69 6f 6e 49  64 22 3a 22 32 36 39 35  |icationId":"2695|
00000020  62 32 63 39 2d 39 36 65  66 2d 34 66 65 34 2d 39  |b2c9-96ef-4fe4-9|
00000030  36 66 38 2d 62 61 32 30  64 30 61 30 32 30 62 33  |6f8-ba20d0a020b3|
00000040  22 7d 7d 29 2e 6d 6f 72  65 4f 6e 54 68 69 73 41  |"}}).moreOnThisA|
00000050  72 74 69 63 6c 65 73 2e  32 2e 6d 6f 72 65 4f 6e  |rticles.2.moreOn|
00000060  54 68 69 73 41 72 74 69  63 6c 65 73 2e 30 2e 69  |ThisArticles.0.i|
00000070  6d 61 67 65 73 2e 30 e5  e5 e5 e5 e5 e5 e5 e5 e5  |mages.0.........|
00000080  24 52 4f 4f 54 5f 51 55  45 52 59 2e 63 6f 6e 74  |$ROOT_QUERY.cont|
00000090  65 6e 74 28 7b 22 63 6f  6e 74 65 6e 74 54 79 70  |ent({"contentTyp|
000000a0  65 22 3a 22 41 72 74 69  63 6c 65 22 2c 22 66 69  |e":"Article","fi|
000000b0  6c 74 65 72 22 3a 7b 22  65 6e 74 69 74 79 55 75  |lter":{"entityUu|
000000c0  69 64 22 3a 22 64 63 34  30 66 31 66 61 2d 35 32  |id":"dc40f1fa-52|
000000d0  61 64 2d 31 31 65 61 2d  38 39 34 38 2d 63 39 61  |ad-11ea-8948-c9a|
000000e0  38 64 38 66 39 62 36 36  37 22 2c 22 61 70 70 6c  |8d8f9b667","appl|
000000f0  69 63 61 74 69 6f 6e 49  64 22 3a 22 32 36 39 35  |icationId":"2695|
00000100  62 32 63 39 2d 39 36 65  66 2d 34 66 65 34 2d 39  |b2c9-96ef-4fe4-9|
00000110  36 66 38 2d 62 61 32 30  64 30 61 30 32 30 62 33  |6f8-ba20d0a020b3|
00000120  22 7d 7d 29 2e 6d 6f 72  65 4f 6e 54 68 69 73 41  |"}}).moreOnThisA|
00000130  72 74 69 63 6c 65 73 2e  32 2e 6d 6f 72 65 4f 6e  |rticles.2.moreOn|
00000140  54 68 69 73 41 72 74 69  63 6c 65 73 2e 31 2e 69  |ThisArticles.1.i|
00000150  6d 61 67 65 73 2e 30 e5  e5 e5 e5 e5 e5 e5 e5 e5  |mages.0.........|
00000160  24 52 4f 4f 54 5f 51 55  45 52 59 2e 63 6f 6e 74  |$ROOT_QUERY.cont|
00000170  65 6e 74 28 7b 22 63 6f  6e 74 65 6e 74 54 79 70  |ent({"contentTyp|
00000180  65 22 3a 22 41 72 74 69  63 6c 65 22 2c 22 66 69  |e":"Article","fi|
00000190  6c 74 65 72 22 3a 7b 22  65 6e 74 69 74 79 55 75  |lter":{"entityUu|
000001a0  69 64 22 3a 22 64 63 34  30 66 31 66 61 2d 35 32  |id":"dc40f1fa-52|
000001b0  61 64 2d 31 31 65 61 2d  38 39 34 38 2d 63 00 fe  |ad-11ea-8948-c..|
000001c0  c2 ff 83 fe c2 ff 02 00  00 00 00 20 bf 1d 00 00  |........... ....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f3 06 b4 42 eb 15 eb 02  |...t.f.....B....|
00000070  31 c9 5a 51 b4 08 cd 13  5b 0f b6 c6 40 50 83 e1  |1.ZQ....[...@P..|
00000080  3f 51 f7 e1 53 52 50 bb  00 7c b9 04 00 66 a1 b0  |?Q..SRP..|...f..|
00000090  07 e8 44 00 0f 82 80 00  66 40 80 c7 02 e2 f2 66  |..D.....f@.....f|
000000a0  81 3e 40 7c fb c0 78 70  75 09 fa bc ec 7b ea 44  |.>@|..xpu....{.D|
000000b0  7c 00 00 e8 83 00 69 73  6f 6c 69 6e 75 78 2e 62  ||.....isolinux.b|
000000c0  69 6e 20 6d 69 73 73 69  6e 67 20 6f 72 20 63 6f  |in missing or co|
000000d0  72 72 75 70 74 2e 0d 0a  66 60 66 31 d2 66 03 06  |rrupt...f`f1.f..|
000000e0  f8 7b 66 13 16 fc 7b 66  52 66 50 06 53 6a 01 6a  |.{f...{fRfP.Sj.j|
000000f0  10 89 e6 66 f7 36 e8 7b  c0 e4 06 88 e1 88 c5 92  |...f.6.{........|
00000100  f6 36 ee 7b 88 c6 08 e1  41 b8 01 02 8a 16 f2 7b  |.6.{....A......{|
00000110  cd 13 8d 64 10 66 61 c3  e8 1e 00 4f 70 65 72 61  |...d.fa....Opera|
00000120  74 69 6e 67 20 73 79 73  74 65 6d 20 6c 6f 61 64  |ting system load|
00000130  20 65 72 72 6f 72 2e 0d  0a 5e ac b4 0e 8a 3e 62  | error...^....>b|
00000140  04 b3 07 cd 10 3c 0a 75  f1 cd 18 f4 eb fd 00 00  |.....<.u........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  c4 20 40 00 00 00 00 00  ae 06 f0 15 00 00 80 00  |. @.............|
000001c0  01 00 00 a1 e0 fe 00 00  00 00 c0 eb 50 00 00 fe  |............P...|
000001d0  ff ff ef fe ff ff b0 6e  40 00 00 1f 00 00 00 2d  |.......n@......-|
000001e0  64 4a 83 59 cc cd 00 f0  50 00 80 a9 9d 00 00 00  |dJ.Y....P.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

 Thanks in advance for help.

---

### Post by yancek on 2020-05-10
Your output does not include a lot of information which usually shows in boot repair.  You have a vfat partition (sda1) at the beginning of the drive which is a windows filesystem and would not be there with any Linux install.  Did you previously have another OS (windows) installed as that may have been an EFI partition.  Scrolling down to line 193 you can see that sda1 is an EFI partition.  You have a Legacy install drive shown by the fact that you have an Extended partition (sda2) which would not exist with a GPT drive.

You indicate you 'messed up' your boot partition but in fact, you have no separate boot partition.  Are you referring to sda1 which is/was an EFI partition?  It should contain EFI boot files for Ubuntu but none show in boot repair.  You may need to re-install Grub as it hasn't installed properly.  I would suggest that you read the Ubuntu documentation at the link below as it discusses EFI installs.  For some reason, the boot repair output does not indicate whether your drive is GPT.

---

### Post by monkeybrain20122 on 2020-05-10
Hi, yes, it is mbr and this machine comes with windows 8 so the vfat (sda1) could be a efi partition for Windows but I couldn't remember since I wiped Windows long time ago and installed Ubuntu. Recently I made a clean install of Ubuntu 20.04 just using default settings with the live usb  (erased 18.04) It was working great for a few days then I did something while trying to clone the file system and end up with a black screen, on reboot I got the grub > prompt I tried reinstall grub with


```

sudo mount /mnt /dev/sda5

sduo grub-install --root-directory=/mnt /dev/sda


```

but didn't help, still got the grub >prompt


grub was installed in /dev/sda1 somehow. I deleted it and now get the please insert a floppy error. Boot-repair didn't work (and boot-repair keeps complaining the usb is almost full)

---

### Post by monkeybrain20122 on 2020-05-10
So I tried

```
sudo mount /mnt /dev/sda5
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

Still no dice, still get the rescue > prompt like before, seems that grub is installed in /dev/sda1 (the vfat partition)

---

### Post by monkeybrain20122 on 2020-05-12
Ok, nevermind. I have reinstalled.

---

