---
title: "Help installing Ubuntu: Gparted does not see my partitions"
date: 2014-03-28
forum: General Help
---

### Post by obake2 on 2014-03-28
I have a laptop that I bought from System76. It came with two drive. On loading ubuntu trusty with daily iso, gparted does not show all the partitions on my drives. See attached screenshot..


The first drive (ext4) is a 240 GB Crucial M500 Series **mSATA** Solid State Drive which Nautilus reports as having  231 GB of capacity.
The second drive is a 500 GB 5400 RPM SATA II 

Ubuntu is installed 13.10 64-bit is installed on the first drive, and the second drive has some personal files.

What sould I do?
```
ubuntu-gnome@ubuntu-gnome:~$ sudo parted /dev/sdc print
Model: PNY USB 2.0 FD (scsi)
Disk /dev/sdc: 8076MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  8070MB  8070MB  primary  fat32        boot, lba


```
```
ubuntu-gnome@ubuntu-gnome:~$ fdisk -lu /dev/sdc
Cannot open /dev/sdc
ubuntu-gnome@ubuntu-gnome:~$ sudo fdisk -lu /dev/sdc

Disk /dev/sdc: 8076 MB, 8076132352 bytes
249 heads, 62 sectors/track, 1021 cylinders, total 15773696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006c593

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62    15762197     7881068    c  W95 FAT32 (LBA)
ubuntu-gnome@ubuntu-gnome:~$
```

```
ubuntu-gnome@ubuntu-gnome:~$  sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000b2376

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   460472319   230235136   83  Linux
/dev/sdb2       460472320   468860927     4194304   82  Linux swap / Solaris

Disk /dev/sdc: 8076 MB, 8076132352 bytes
249 heads, 62 sectors/track, 1021 cylinders, total 15773696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006c593

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62    15762197     7881068    c  W95 FAT32 (LBA)
ubuntu-gnome@ubuntu-gnome:~$ 


```

---

### Post by reyals140 on 2014-03-28
Maybe I'm blind... but what exactly is missing?

---

### Post by obake2 on 2014-03-29
What's missing is 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   460472319   230235136   83  Linux
/dev/sdb2       460472320   468860927     4194304   82  Linux swap / Solaris

It dosn't show i gparted.

Anyways. I just in case run the Installer to see if that detects it and it did. I went ahead and installed but at the end it said "Fatal error" couldn't install boot flag in chosen location. Something along those lines.
And now after I reboot the computer, the whole screen is black and blinking, and nothing loads. :(

---

### Post by fantab on 2014-03-29
Boot with Ubuntu DVD/USB, Try Ubuntu without installing and post the output of:
```
sudo parted -l
```

---

### Post by obake2 on 2014-03-29
```
ubuntu-gnome@ubuntu-gnome:~$ sudo parted -l
Model: ATA WDC WD5000LPVX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size   File system  Name     Flags
 1      1049kB  500GB  500GB  ext4         primary


Model: ATA Crucial_CT240M50 (scsi)
Disk /dev/sdb: 240GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2
 2      257MB   240GB  240GB  extended
 5      257MB   240GB  240GB  logical


Model: PNY USB 2.0 FD (scsi)
Disk /dev/sdc: 8076MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  8070MB  8070MB  primary  fat32        boot, lba


Error: /dev/mapper/ubuntu--gnome--vg-swap_1: unrecognised disk label      

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--gnome--vg-root: 236GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  236GB  236GB  ext4


Error: /dev/mapper/sdb5_crypt: unrecognised disk label                    

ubuntu-gnome@ubuntu-gnome:~$
```

---

### Post by obake2 on 2014-03-29
Script from [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

[http://pastebin.ubuntu.com/7172873/](http://pastebin.ubuntu.com/7172873/)

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20130620
    Boot sector info:  Syslinux looks at sector 1895848 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdc1 starts at sector 
                       0. But according to the info from fdisk, sdc1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

ubuntu-gnome-vg-root': _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

ubuntu-gnome-vg-swap_1': _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048   976,771,071   976,769,024 Data partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048       499,711       497,664  83 Linux
/dev/sdb2             501,758   468,860,927   468,359,170   5 Extended
/dev/sdb5             501,760   468,860,927   468,359,168  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 8076 MB, 8076132352 bytes
249 heads, 62 sectors/track, 1021 cylinders, total 15773696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62    15,762,197    15,762,136   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       4b7aa90e-6b81-4851-aa08-b7094d142a3c   ext3       
/dev/mapper/sdb5_crypt t0t8Xn-GDeJ-4AIY-tBAA-n2PT-dCvy-zNzqT2 LVM2_member 
/dev/mapper/ubuntu--gnome--vg-root b1b2e59f-547e-4345-839f-55bb9b5c3704   ext4       
/dev/sda1        c80b68f7-a856-4b18-9544-68bba814561c   ext4       Extra Drive 1
/dev/sdb1        bc79b92d-6a64-42bd-ba1a-c039d6280a2c   ext2       
/dev/sdb5        b3efb905-818c-4a49-a04a-ee46f41fe32e   crypto_LUKS 
/dev/sdc1        7D30-ACB3                              vfat       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
sdb5_crypt
ubuntu--gnome--vg-root
ubuntu--gnome--vg-swap_1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/ubuntu--gnome--vg-root /target                  ext4       (rw,errors=remount-ro)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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

menuentry "Try Ubuntu GNOME without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu-gnome.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu GNOME" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu-gnome.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu-gnome.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  31 35 61 32 62 36 38 31  32 66 33 36 64 37 66 33  |15a2b6812f36d7f3|
00000010  30 61 39 35 64 37 63 65  35 30 38 32 36 37 34 32  |0a95d7ce50826742|
00000020  66 0a 53 48 41 32 35 36  3a 20 66 36 38 36 34 37  |f.SHA256: f68647|
00000030  64 32 66 63 36 66 32 62  36 62 63 66 34 39 39 66  |d2fc6f2b6bcf499f|
00000040  64 33 63 35 35 66 36 31  66 32 39 36 36 30 62 37  |d3c55f61f29660b7|
00000050  31 34 32 30 62 63 65 32  36 63 34 34 36 64 38 31  |1420bce26c446d81|
00000060  38 64 35 37 61 32 33 39  38 39 0a 44 65 73 63 72  |8d57a23989.Descr|
00000070  69 70 74 69 6f 6e 3a 20  47 61 6d 62 61 73 20 52  |iption: Gambas R|
00000080  50 43 20 63 6f 6d 70 6f  6e 65 6e 74 0a 48 6f 6d  |PC component.Hom|
00000090  65 70 61 67 65 3a 20 68  74 74 70 3a 2f 2f 67 61  |epage: http://ga|
000000a0  6d 62 61 73 2e 73 6f 75  72 63 65 66 6f 72 67 65  |mbas.sourceforge|
000000b0  2e 6e 65 74 0a 44 65 73  63 72 69 70 74 69 6f 6e  |.net.Description|
000000c0  2d 6d 64 35 3a 20 62 62  62 34 31 38 63 37 30 34  |-md5: bbb418c704|
000000d0  39 33 30 30 35 64 32 33  64 38 33 33 62 65 63 38  |93005d23d833bec8|
000000e0  63 65 65 39 34 65 0a 42  75 67 73 3a 20 68 74 74  |cee94e.Bugs: htt|
000000f0  70 73 3a 2f 2f 62 75 67  73 2e 6c 61 75 6e 63 68  |ps://bugs.launch|
00000100  70 61 64 2e 6e 65 74 2f  75 62 75 6e 74 75 2f 2b  |pad.net/ubuntu/+|
00000110  66 69 6c 65 62 75 67 0a  4f 72 69 67 69 6e 3a 20  |filebug.Origin: |
00000120  55 62 75 6e 74 75 0a 0a  50 61 63 6b 61 67 65 3a  |Ubuntu..Package:|
00000130  20 67 61 6d 62 61 73 33  2d 67 62 2d 78 6d 6c 2d  | gambas3-gb-xml-|
00000140  78 73 6c 74 0a 50 72 69  6f 72 69 74 79 3a 20 6f  |xslt.Priority: o|
00000150  70 74 69 6f 6e 61 6c 0a  53 65 63 74 69 6f 6e 3a  |ptional.Section:|
00000160  20 75 6e 69 76 65 72 73  65 2f 6c 69 62 64 65 76  | universe/libdev|
00000170  65 6c 0a 49 6e 73 74 61  6c 6c 65 64 2d 53 69 7a  |el.Installed-Siz|
00000180  65 3a 20 33 39 0a 4d 61  69 6e 74 61 69 6e 65 72  |e: 39.Maintainer|
00000190  3a 20 55 62 75 6e 74 75  20 44 65 76 65 6c 6f 70  |: Ubuntu Develop|
000001a0  65 72 73 20 3c 75 62 75  6e 74 75 2d 64 65 76 65  |ers <ubuntu-deve|
000001b0  6c 2d 64 69 73 63 75 73  73 40 6c 69 73 74 00 3b  |l-discuss@list.;|
000001c0  1d 1f 83 fe ff ff 02 00  00 00 00 98 ea 1b 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb5

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  78 74 73 2d 70 6c 61 69  |........xts-plai|
00000030  6e 36 34 00 00 00 00 00  00 00 00 00 00 00 00 00  |n64.............|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 10 00 00 00 00 40  |...............@|
00000070  d2 a7 a3 b4 d0 f3 13 56  8d 7d f2 fb d3 5c d2 ed  |.......V.}...\..|
00000080  b5 1e f0 1b a7 08 20 f2  57 8c e3 74 b4 ef 6a c8  |...... .W..t..j.|
00000090  05 67 a1 5f 53 7c dd 01  08 67 d5 2c 58 bd cf 82  |.g._S|...g.,X...|
000000a0  d5 c7 3d 48 00 00 e6 f5  62 33 65 66 62 39 30 35  |..=H....b3efb905|
000000b0  2d 38 31 38 63 2d 34 61  34 39 2d 61 30 34 61 2d  |-818c-4a49-a04a-|
000000c0  65 65 34 36 66 34 31 66  65 33 32 65 00 00 00 00  |ee46f41fe32e....|
000000d0  00 ac 71 f3 00 03 a3 18  ac a9 4f 7f 09 e5 a8 9d  |..q.......O.....|
000000e0  bb f0 48 9a 48 f7 22 56  7f f9 0f 26 a5 f2 5c 8a  |..H.H."V...&..\.|
000000f0  ba c0 06 83 fc c3 06 c1  00 00 00 08 00 00 0f a0  |................|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 02 00 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 03 f8 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 05 f0 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 07 e8 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 09 e0 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader on ubuntu-gnome-vg-root'


Unknown BootLoader on ubuntu-gnome-vg-swap_1'



=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-yke95RWv/Tmp_Log: No such file or directory
bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo-yke95RWv/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-yke95RWv/Tmp_Log: No such file or directory
  skip_dev_dir: Couldn't split up device name ubuntu-gnome-vg-root'
  Volume group name ubuntu-gnome-vg-root' has invalid characters
  Skipping volume group ubuntu-gnome-vg-root'
  skip_dev_dir: Couldn't split up device name ubuntu-gnome-vg-root'
  Volume group name ubuntu-gnome-vg-root' has invalid characters
  Skipping volume group ubuntu-gnome-vg-root'
  skip_dev_dir: Couldn't split up device name ubuntu-gnome-vg-root'
  Volume group name ubuntu-gnome-vg-root' has invalid characters
  Skipping volume group ubuntu-gnome-vg-root'
hexdump: /dev/mapper/ubuntu-gnome-vg-root': No such file or directory
hexdump: /dev/mapper/ubuntu-gnome-vg-root': No such file or directory
  skip_dev_dir: Couldn't split up device name ubuntu-gnome-vg-swap_1'
  Volume group name ubuntu-gnome-vg-swap_1' has invalid characters
  Skipping volume group ubuntu-gnome-vg-swap_1'
  skip_dev_dir: Couldn't split up device name ubuntu-gnome-vg-swap_1'
  Volume group name ubuntu-gnome-vg-swap_1' has invalid characters
  Skipping volume group ubuntu-gnome-vg-swap_1'
  skip_dev_dir: Couldn't split up device name ubuntu-gnome-vg-swap_1'
  Volume group name ubuntu-gnome-vg-swap_1' has invalid characters
  Skipping volume group ubuntu-gnome-vg-swap_1'
hexdump: /dev/mapper/ubuntu-gnome-vg-swap_1': No such file or directory
hexdump: /dev/mapper/ubuntu-gnome-vg-swap_1': No such file or directory


```

---

### Post by Mark Phelps on 2014-03-29
Unless I'm misreading the screenshot, there is a button on the upper right area that you have to click to select the other drive.  It only shows one drive at a time -- that's how it works.  All the command line results clearly show both drives.  Don't see anything missing.

---

