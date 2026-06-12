---
title: "update to ubuntu mate 18 totally messed up dual boot"
date: 2020-03-17
forum: General Help
---

### Post by DVD-R on 2020-03-17
Hello All,
I had Windows 7 Pro and Ubuntu Mate 14 dual boot in a thinkpad.
Today I decided to replace Ubuntu 14 with Ubuntu Mate 18
I have the install media on thumb-drive and used it to create a virtual Ubuntu to check out Mate 18

Installed Mate 18 over Mate 14.
And now the thinkpad just cycles over and over at boot up
I tried fixing it with a Grub-boot repair a couple of times - without success.

I'm thinking I might try to put another hard drive in the unit and create a small boot partition.
Then install Ubuntu Mate 18
Then clone my current Windows partition into that drive.
Then update grub.

Unless anyone else has any other ideas

Thanks

---

### Post by yancek on 2020-03-17
If you can't solve your problem and already have boot repair, why not run it with the Create BootInfo Summary option and post the link here where are people with a lot more knowledge available to view it?

---

### Post by DVD-R on 2020-03-17
Ok, thanks - I'll do that.

BTW: I've found that I can boot up using Hiram and then use one of the boot loader apps in that to get into Windows.
One of the partitions is NTFS - for windows
There is a 100meg partition for the MBR
And the Ubuntu partition should be EXT4

And here is the boot info summary

 

```
Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda1: unknown filesystem type ''.

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda1: unknown filesystem type ''.
mount: /mnt/BootInfo/sda2: unknown filesystem type ''.

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda1: unknown filesystem type ''.
mount: /mnt/BootInfo/sda2: unknown filesystem type ''.
mount: /mnt/BootInfo/sda5: unknown filesystem type ''.

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda1: unknown filesystem type ''.
mount: /mnt/BootInfo/sda2: unknown filesystem type ''.
mount: /mnt/BootInfo/sda5: unknown filesystem type ''.
mount: /mnt/BootInfo/sda6: unknown filesystem type ''.

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 8200 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1     ?         2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   251,138,047   250,931,200   7 NTFS / exFAT / HPFS
/dev/sda3         251,140,094   312,580,095    61,440,002   5 Extended
/dev/sda5         251,140,096   252,188,671     1,048,576  ef EFI (FAT-12/16/32)
/dev/sda6         252,190,720   312,580,095    60,389,376  83 Linux


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 961 MiB, 1007681536 bytes, 1968128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     1,968,127     1,966,080   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        9095-7161                              vfat       BOOT-REPAIR
/dev/zram0       051a19f7-3ac6-4389-9136-0bdc79ec0ea2   swap       
/dev/zram1       9d2fea18-08ed-4af9-a3b5-2129d8679a6c   swap       
/dev/zram2       9b750027-5233-4b2d-b5b9-a2f7d180cfea   swap       
/dev/zram3       d48293f9-d41c-48ab-9d9c-580501c05113   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Mar 18 01:52 ata-INTEL_SSDSA2BW160G3H_CVPR145206EF160DGN -> ../../sda
lrwxrwxrwx 1 root root 10 Mar 18 01:52 ata-INTEL_SSDSA2BW160G3H_CVPR145206EF160DGN-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Mar 18 01:51 ata-PLDS_DVD-RW_DS8A8SH_S45N7602Z1ZM1R00VP1V -> ../../sr0
lrwxrwxrwx 1 root root  9 Mar 18 01:52 usb-General_UDisk-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Mar 18 01:52 usb-General_UDisk-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Mar 18 01:52 wwn-0x5001517bb27202b4 -> ../../sda
lrwxrwxrwx 1 root root 10 Mar 18 01:52 wwn-0x5001517bb27202b4-part2 -> ../../sda2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Boot-Repair-Disk session" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2

00000000  66 69 6c 61 73 20 61 64  6d 69 74 69 64 61 73 20  |filas admitidas |
00000010  28 6f 70 63 69 6f 6e 61  6c 29 01 05 4c 49 4d 49  |(opcional)..LIMI|
00000020  54 01 0e 4c 49 4d 49 54  20 79 20 4f 46 46 53 45  |T..LIMIT y OFFSE|
00000030  54 01 09 28 6e 69 6e 67  75 6e 6f 29 01 03 54 4f  |T..(ninguno)..TO|
00000040  50 01 09 28 4e 69 6e 67  75 6e 6f 29 01 05 49 6d  |P..(Ninguno)..Im|
00000050  70 61 72 01 07 41 63 65  70 74 61 72 01 5d 4e 6f  |par..Aceptar.]No|
00000060  20 73 65 20 68 61 20 70  6f 64 69 64 6f 20 6d 6f  | se ha podido mo|
00000070  73 74 72 61 72 20 65 6c  20 67 65 6e 65 72 61 64  |strar el generad|
00000080  6f 72 20 64 65 20 63 61  64 65 6e 61 73 20 64 65  |or de cadenas de|
00000090  20 63 6f 6e 65 78 69 c3  b3 6e 20 64 65 62 69 64  | conexi..n debid|
000000a0  6f 20 61 6c 20 73 69 67  75 69 65 6e 74 65 20 65  |o al siguiente e|
000000b0  72 72 6f 72 3a 20 22 7b  30 7d 22 01 38 4e 6f 20  |rror: "{0}".8No |
000000c0  73 65 20 70 75 65 64 65  20 6d 6f 73 74 72 61 72  |se puede mostrar|
000000d0  20 65 6c 20 67 65 6e 65  72 61 64 6f 72 20 64 65  | el generador de|
000000e0  20 63 61 64 65 6e 61 73  20 64 65 20 63 6f 6e 65  | cadenas de cone|
000000f0  78 69 c3 b3 6e 01 06 31  20 62 79 74 65 01 14 31  |xi..n..1 byte..1|
00000100  20 76 61 6c 6f 72 20 73  65 6c 65 63 63 69 6f 6e  | valor seleccion|
00000110  61 64 6f 01 1c 53 6f 6c  6f 20 65 6c 65 6d 65 6e  |ado..Solo elemen|
00000120  74 6f 73 20 73 65 6c 65  63 63 69 6f 6e 61 64 6f  |tos seleccionado|
00000130  73 01 12 41 62 72 69 72  20 61 72 63 68 69 76 6f  |s..Abrir archivo|
00000140  20 63 6f 6d 6f 01 08 4f  70 65 72 61 64 6f 72 01  | como..Operador.|
00000150  2b 44 65 74 61 6c 6c 65  73 20 64 65 6c 20 6f 70  |+Detalles del op|
00000160  65 72 61 64 6f 72 20 70  61 72 61 20 6c 61 20 63  |erador para la c|
00000170  6c c3 a1 75 73 75 6c 61  20 7b 30 7d 01 1e 4f 70  |l..usula {0}..Op|
00000180  65 72 61 64 6f 72 20 70  61 72 61 20 6c 61 20 63  |erador para la c|
00000190  6c c3 a1 75 73 75 6c 61  20 7b 30 7d 01 08 4f 70  |l..usula {0}..Op|
000001a0  63 69 6f 6e 65 73 01 06  43 75 65 6e 74 61 01 2d  |ciones..Cuenta.-|
000001b0  53 65 72 76 69 63 69 6f  73 20 64 65 20 61 75 74  |Servicios de aut|
000001c0  65 6e 74 69 63 61 63 69  c3 b3 6e 20 64 65 20 41  |enticaci..n de A|
000001d0  44 46 53 20 61 70 72 6f  62 61 64 6f 73 01 da 01  |DFS aprobados...|
000001e0  44 75 72 61 6e 74 65 20  65 6c 20 69 6e 69 63 69  |Durante el inici|
000001f0  6f 20 64 65 20 73 65 73  69 c3 b3 6e 20 73 65 20  |o de sesi..n se |
00000200

Unknown BootLoader on sda3


Unknown BootLoader on sda5


Unknown BootLoader on sda6



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory

ADDITIONAL INFORMATION :
=================== log of boot-repair 20200318_0152 ===================
boot-repair version : 4ppa62
boot-sav version : 4ppa62
boot-sav-extra version : 4ppa62
glade2script version : 3.2.3~ppa4
Error: /dev/sda: unrecognised disk label
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 1oct2017, zesty, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
ls: cannot access '/home/usr/.config': No such file or directory

=================== os-prober:


=================== blkid:
/dev/sdb1: LABEL="BOOT-REPAIR" UUID="9095-7161" TYPE="vfat" PARTUUID="01d15f29-01"
/dev/loop0: TYPE="squashfs"
/dev/zram0: UUID="051a19f7-3ac6-4389-9136-0bdc79ec0ea2" TYPE="swap"
/dev/zram1: UUID="9d2fea18-08ed-4af9-a3b5-2129d8679a6c" TYPE="swap"
/dev/zram2: UUID="9b750027-5233-4b2d-b5b9-a2f7d180cfea" TYPE="swap"
/dev/zram3: UUID="d48293f9-d41c-48ab-9d9c-580501c05113" TYPE="swap"

/usr/share/boot-sav/bs-cmd_terminal.sh: line 179: warning: command substitution: ignored null byte in input

=================== efibootmgr -v
BootCurrent: 000D
Timeout: 2 seconds
BootOrder: 0000,0001,0002,0003,0007,0008,000A,000B,000C,000D,0009,000E,000F,0011,0010,0012
Boot0000  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0001  Boot Menu    FvFile(126a762d-5758-4fca-8531-201a7f57f850)
Boot0002  Diagnostic Splash Screen    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0003  Lenovo Diagnostics    FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
Boot0004  Startup Interrupt Menu    FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
Boot0005  ME Configuration Menu    FvFile(82988420-7467-4490-9059-feb448dd1963)
Boot0006  Rescue and Recovery    FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
Boot0007  USB CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot0008  USB FDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot0009* ATAPI CD0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a35401)
Boot000A* ATA HDD0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)
Boot000B  ATA HDD1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)
Boot000C  ATA HDD2    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f602)
Boot000D* USB HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot000E  PCI LAN    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot000F  ATAPI CD1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a35404)
Boot0010  Other CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a35406)
Boot0011  ATA HDD3    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f604)
Boot0012  Other HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f606)
Boot0013* IDER BOOT CDROM    PciRoot(0x0)/Pci(0x16,0x2)/Ata(0,1,0)
Boot0014* IDER BOOT Floppy    PciRoot(0x0)/Pci(0x16,0x2)/Ata(0,0,0)
Boot0015* ATA HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f6)
Boot0016* ATAPI CD:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a354)
Boot0017* PCI LAN    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot0018* Windows Boot Manager    HD(2,GPT,893688a4-26b2-4270-aac2-6788a1e8425d,0x18e800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0019* Windows Boot Manager    HD(2,GPT,817366e4-e523-4bca-b126-026725c6f367,0x300800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot001A* ubuntu    HD(5,MBR,0xa6a7c230,0x0,0x0)/File(EFIubuntushimx64.efi)
Boot001B* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot001C* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot001D* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot001E* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot001F* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0020* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0021* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0022* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0023* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0024* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0025* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0026* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0027* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0028* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0029* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot002A* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot002B* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot002C* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot002D* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot002E* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot002F* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0030* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0031* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0032* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0033* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0034* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0035* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0036* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0037* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0038* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0039* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot003A* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot003B* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot003C* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot003D* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot003E* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot003F* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0040* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0041* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0042* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0043* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0044* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0045* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0046* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0047* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0048* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0049* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot004A* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot004B* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot004C* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot004D* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot004E* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot004F* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0050* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0051* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0052* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0053* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0054* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)
Boot0055* ubuntu    HD(3,MBR,0xa6a7c230,0xef817fe,0x3a98002)/HD(1,MBR,0x0,0xef81800,0x100000)/File(EFIubuntushimx64.efi)

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:



=================== parted -lm:

BYT;
/dev/sda:160GB:scsi:512:512:unknown:ATA INTEL SSDSA2BW16:;

BYT;
/dev/sdb:1008MB:scsi:512:512:msdos:General UDisk:;
1:1049kB:1008MB:1007MB:fat32::boot, lba;

BYT;
/dev/zram3:2079MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:2079MB:2079MB:linux-swap(v1)::;

BYT;
/dev/zram1:2079MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:2079MB:2079MB:linux-swap(v1)::;

BYT;
/dev/zram2:2079MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:2079MB:2079MB:linux-swap(v1)::;

BYT;
/dev/zram0:2079MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:2079MB:2079MB:linux-swap(v1)::;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
loop0 loop squashfs 629.3M
sda   disk          149.1G
sda2  part            7.3G
sdb   disk            961M
sdb1  part vfat       960M BOOT-REPAIR
sr0   rom            1024M
zram0 disk              2G
zram1 disk              2G
zram2 disk              2G
zram3 disk              2G

KNAME ROTA RO RM STATE   MOUNTPOINT
loop0    1  1  0         /rofs
sda      0  0  0 running
sda2     0  0  0
sdb      1  0  1 running
sdb1     1  0  1         /cdrom
sr0      1  0  1 running
zram0    0  0  0         [SWAP]
zram1    0  0  0         [SWAP]
zram2    0  0  0         [SWAP]
zram3    0  0  0         [SWAP]


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8094980k,nr_inodes=2023745,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1624436k,mode=755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=31,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=13073)
mqueue on /dev/mqueue type mqueue (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=1624432k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda2 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 drm_dp_aux1 drm_dp_aux2 dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 initctl input kmsg kvm lightnvm log mapper mcelog media0 mei0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx ptp0 pts random rfkill rtc rtc0 sda sda2 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout tpm0 uhid uinput urandom usb userio v4l vfio vga_arbiter vhci vhost-net vhost-vsock video0 zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.8G     0  7.8G   0% /dev
tmpfs          tmpfs     1.6G  9.3M  1.6G   1% /run
/dev/sdb1      vfat      956M  708M  249M  74% /cdrom
/dev/loop0     squashfs  630M  630M     0 100% /rofs
/cow           overlay   7.8G  3.9M  7.8G   1% /
tmpfs          tmpfs     7.8G     0  7.8G   0% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.8G     0  7.8G   0% /sys/fs/cgroup
tmpfs          tmpfs     7.8G  4.0K  7.8G   1% /tmp
tmpfs          tmpfs     1.6G  4.0K  1.6G   1% /run/user/999

=================== fdisk -l:
Disk /dev/loop0: 629.3 MiB, 659873792 bytes, 1288816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xa6a7c230

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848 251138047 250931200 119.7G  7 HPFS/NTFS/exFAT
/dev/sda3       251140094 312580095  61440002  29.3G  5 Extended
/dev/sda5       251140096 252188671   1048576   512M ef EFI (FAT-12/16/32)
/dev/sda6       252190720 312580095  60389376  28.8G 83 Linux




Disk /dev/sdb: 961 MiB, 1007681536 bytes, 1968128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x01d15f29

Device     Boot Start     End Sectors  Size Id Type
/dev/sdb1  *     2048 1968127 1966080  960M  c W95 FAT32 (LBA)


Disk /dev/zram0: 2 GiB, 2079272960 bytes, 507635 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram1: 2 GiB, 2079272960 bytes, 507635 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram2: 2 GiB, 2079272960 bytes, 507635 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram3: 2 GiB, 2079272960 bytes, 507635 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Error: no partitions

** (zenity:5944): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2020-03-17
Please use code tags, easy to add with Forum's Advanced Editor and # icon.
And with Boot-Repair you want to use latest version in Ubuntu live installer by adding ppa and then just post link not report.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You show MBR(msdos) partitions, but with corruption in every one.
But have both many, many Ubuntu and Windows UEFI boot entries and then would have had gpt partitioning.
Did you force a change to MBR from gpt?

Some systems lock up with too many UEFI entries. You must houseclean all the duplicates.

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/ ]("http://software.intel.com/en-us/articles/efi-shells-and-scripting/")

---

### Post by DVD-R on 2020-03-18
Thank you very much!

I'm booted in Ubuntu 18 USB - installed boot repair - and here is the URL for the report:
[http://paste.ubuntu.com/p/T4X3JMhzmF/](http://paste.ubuntu.com/p/T4X3JMhzmF/)

I also used efibootmgr to delete  a large number of duplicate boot entries that were obviously erroneous.
And I don't know how they go there.

I tried to restart and the system is still cycling bios startup without a correct boot sequence. 
And I don't know if enough about MBR vs GUID to be able know if they are in conflict and how I should proceed.

But I will check the links you provided and continue by reading up there.
Thanks

---

### Post by yancek on 2020-03-18
You have an msdos partitioned drive (sda) and you have windows code in the MBR so in order to boot Ubuntu, you would need to go through a convoluted process to create an entry with bcdedit on windows to access Ubuntu and boot it.  Problem with this is that you seem to have installed Ubuntu in UEFI mode and windows won't boot it.  You need to install Ubuntu in Legacy mode and install the Ubuntu Grub code to the MBR of that drive.  It should then detect windows and put an entry in the Grub boot menu.  The usual information is not available in your report and your filesystems seem to be corrupted as they are not recognized.  You would need some windows software, an installation DVD or repair disk to run chkdsk on the windows partitions (first 2 partitions on the drive).  You can't do that from Linux.  You might also try running a filesystem check with fsck on the Ubuntu partitions (sda5 and sda6).

You have an astounding number of entries for efi according to the output of efibootmgr.  You don't need any of this and might delete that partition.  You have an msdos disk and windows can't be installed EFI on that.  I see you have EFI entries for windows but I can't image they would work and don't know how  they got there?

---

### Post by oldfred on 2020-03-18
Report still showed all the Ubuntu entries, was that before you housecleaned?
And those show Ubuntu was installed in UEFI mode to MBR drive.
But Windows UEFI boot entry shows it was installed to gpt partitioned drive. Do you have another drive not shown?

And every partition shows errors which is strange. Partition table says dos/MBR and shows partitions, but with the errors no info can be loaded from those partitions?

Do you have good backups of Windows & Ubuntu data?

---

### Post by DVD-R on 2020-03-18
Thanks yancek
I did have this running as a dual boot with Windows and Ubuntu 14.
It was the attempt at installing ubuntu 18 over the ubuntu 14 that I suspect did the damage.
I have a suspicion the Ubuntu 18 install did the UEFI mode automatically - because I don't remember any option from the installer otherwise.

I'll see if I can find information on installing Ubuntu 18 in legacy mode.
I also so more EUFI entries in efibootmgr after I cleaned up and posted that last summary.
So I removed those also.

I wish there was an application that could remove the EUFI from all of the partitions - if it is not needed.

---

### Post by DVD-R on 2020-03-18
Can you help me identify where in the report you are seeing the that Ubuntu was installed in UEFI mode to an MBR drive?
And where in the report can I find Windows UEFI boot entry showing it was installed in gpt partitioned drive.
and by gpt do you mean gparted?

---

### Post by DVD-R on 2020-03-18
Ok, I had some good success!
Using the Hiram usb - I used a boot-loader and booted up into windows.
Then pulled up DOS in administrator mode.
Then loaded up the Disk manager - which showed the Ubuntu partition that was set as EFI
The Disk Manager cannot alter that partition as it is protected.

So I used DISKPART to gain access into that partition and removed the EFI by the SET ID command - and then deleted it with the delete command.
Then looked in Disk Manager and that partition was gone.
Then reboot - and the laptop now boots normally into Windows.

I can only assume the Ubuntu 18 installation process created the EFI partition.
I've installed Ubuntu a bunch of times and its never done this.

But I want to thank you all very much for your help!!

---

### Post by oldfred on 2020-03-18
How you boot install media, UEFI or BIOS is then how it installs.
All systems since Windows 8 released in  2012 are UEFI but have CSM mode.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

If newer UEFI hardware may be better to install Windows in UEFI boot mode. Or at least plan to in future.

Ubuntu will let you install in UEFI mode to a MBR drive and really should not, especially if Windows is on that drive.
Windows in BIOS/MBR mode requires boot flag on its boot partition. But UEFI requires boot flag on the ESP for UEFI boot. And you only can have one boot flag per drive.

UEFI normally uses gpt partitioning & Windows requires gpt with UEFI boot.

---

### Post by yancek on 2020-03-18
Dual booting with windows 10 in UEFI is explained at the site below which is the official Ubuntu documentation.  It also tells you how you can tell if you are booting UEFI or Legacy as well as a lot of other useful information.  If you boot UEFI, it will install UEFI and will create the EFI partition if none exists.  You don't want that on the msdos dirve so make sure you boot Legacy if you install again. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> Can you help me identify where in the report you are seeing the that Ubuntu was installed in UEFI mode to an MBR drive? 

Line 73 of the boot repair report shows:  Disklabel type: dos
Lines 64 & 479 show EFI and beginning at line 261 you see a large number of efi entries.

If you decide to install Ubuntu, I would make sure to read the link I posted above.

---

### Post by oldfred on 2020-03-18
Line 290 & up show UEFI boot entries, and MBR partition. UEFI boot file is  EFIubuntushimx64.efi. UEFI does not seem to require / or \ for folders & files.

A UEFI install would also show the mount of the ESP - efi system partition in fstab. But since it could not open any partitions, it did not show that file, or any files it normally shows.

---

### Post by DVD-R on 2020-03-19
How do I tag this thread as completed?

---

### Post by oldfred on 2020-03-19
See last line of my signature, below.

---

