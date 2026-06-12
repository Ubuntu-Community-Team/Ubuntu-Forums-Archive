---
title: "ERROR when trying to start Ubuntu 22.04"
date: 2023-06-19
forum: General Help
---

### Post by tjharring on 2023-06-19
I am like many others that are fed up with Windows. I have a multi-boot system with Windows 10, Ubuntu 22.04, Linux Mint 21, and Debian 11. I am trying to decide which version of Linux I am going to switch to. I am very much leaning toward Ubuntu. I have been using this setup for about a year testing each of the OSes. Usually after I login into any them and have been using it for about 20-30 minutes I will open terminal and run the update and upgrade commands. This has always worked well and has never caused any problems. The last time I ran Debian 11 I update and upgrade with no issues.
Yesterday I wanted to login into Ubuntu and when I selected it from GRUB I received the following,
"error: file '/boot/vmlinuz-5.19.0-41-generic' not found
error: file need to load the kernel first.
Press any key to continue..."

The last time I ran Debian it updated GRUB which it has done in the past without issue. I can tell because the background shows Debian logo. I tried to select one of Ubuntu's recovery modes and none work. I am able to go into all other OSes from GRUB except Ubuntu. Any suggestions to fix this would be greatly appreciated.

---

### Post by Rubi1200 on 2023-06-19
Hi,

if you run the boot info script in my signature and post the results here we will hopefully have a better idea of what is going on. Note, do not repair, just post the results please.

---

### Post by coffeecat on 2023-06-19
Two threads merged and *moved to **General Help**,* as they are primarily about Ubuntu. Please do not post the same question in different parts of the forum. This causes confusion and dilutes community effort.

---

### Post by tjharring on 2023-06-19
My apologies.

---

### Post by tjharring on 2023-06-19
I will do this tonight and post results. Thank you in advance.

---

### Post by tjharring on 2023-06-19
> **Rubi1200 said:**
> Hi,

if you run the boot info script in my signature and post the results here we will hopefully have a better idea of what is going on. Note, do not repair, just post the results please.

Can I run the script from either of the other 2 linux OSes I have?

---

### Post by Rubi1200 on 2023-06-19
It might work from Linux Mint, but not sure of that. Easiest is to use a liveUSB to do this.

---

### Post by tjharring on 2023-06-19
> **Rubi1200 said:**
> It might work from Linux Mint, but not sure of that. Easiest is to use a liveUSB to do this.

```
Below is the boot report,

boot-info-4ppa203                                              [20230619_2328] 

 
 
============================== Boot Info Summary ===============================
 

 
 
 => No boot loader is installed in the MBR of /dev/sda.
 

 
 
sda1: __________________________________________________________________________
 

 
 
    File system:       ntfs
 
    Boot sector type:  Windows 8/10/11/2012: NTFS
 
    Boot sector info:  No errors found in the Boot Parameter Block.
 
    Operating System:  
 
    Boot files:        
 

 
 
sda2: __________________________________________________________________________
 

 
 
    File system:       vfat
 
    Boot sector type:  Windows 8/10/11/2012: FAT32
 
    Boot sector info:  No errors found in the Boot Parameter Block.
 
    Operating System:  
 
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbia32.efi 
 
                       /efi/Boot/fbx64.efi /efi/Boot/mmx64.efi 
 
                       /efi/debian/fbx64.efi /efi/debian/grubx64.efi 
 
                       /efi/debian/mmx64.efi /efi/debian/shimx64.efi 
 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
 
                       /efi/ubuntu/shimx64.efi /efi/debian/grub.cfg 
 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
 
                       /efi/Microsoft/Boot/bootmgr.efi
 

 
 
sda3: __________________________________________________________________________
 

 
 
    File system:       
 
    Boot sector type:  -
 
    Boot sector info: 
 

 
 
sda4: __________________________________________________________________________
 

 
 
    File system:       ntfs
 
    Boot sector type:  Windows 8/10/11/2012: NTFS
 
    Boot sector info:  No errors found in the Boot Parameter Block.
 
    Operating System:  Windows 8 or 10
 
    Boot files:        /bootmgr /Windows/System32/winload.exe
 

 
 
sda5: __________________________________________________________________________
 

 
 
    File system:       ntfs
 
    Boot sector type:  Windows 8/10/11/2012: NTFS
 
    Boot sector info:  No errors found in the Boot Parameter Block.
 
    Operating System:  
 
    Boot files:        
 

 
 
sda6: __________________________________________________________________________
 

 
 
    File system:       ext4
 
    Boot sector type:  -
 
    Boot sector info: 
 
    Operating System:  Linux Mint 21.1
 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub
 

 
 
sda7: __________________________________________________________________________
 

 
 
    File system:       ext4
 
    Boot sector type:  -
 
    Boot sector info: 
 
    Operating System:  
 
    Boot files:        
 

 
 
sda8: __________________________________________________________________________
 

 
 
    File system:       swap
 
    Boot sector type:  -
 
    Boot sector info: 
 

 
 
sda9: __________________________________________________________________________
 

 
 
    File system:       ext4
 
    Boot sector type:  -
 
    Boot sector info: 
 
    Operating System:  Debian GNU/Linux 11 (bullseye)
 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub
 

 
 
sda10: _________________________________________________________________________
 

 
 
    File system:       ext4
 
    Boot sector type:  -
 
    Boot sector info: 
 
    Operating System:  
 
    Boot files:        
 

 
 
sda11: _________________________________________________________________________
 

 
 
    File system:       swap
 
    Boot sector type:  -
 
    Boot sector info: 
 

 
 
sda12: _________________________________________________________________________
 

 
 
    File system:       ext4
 
    Boot sector type:  -
 
    Boot sector info: 
 
    Operating System:  Ubuntu 22.04.2 LTS
 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub
 

 
 
sda13: _________________________________________________________________________
 

 
 
    File system:       ext4
 
    Boot sector type:  -
 
    Boot sector info: 
 
    Operating System:  
 
    Boot files:        
 

 
 
sda14: _________________________________________________________________________
 

 
 
    File system:       swap
 
    Boot sector type:  -
 
    Boot sector info: 
 

 
 
sdb: ___________________________________________________________________________
 

 
 
    File system:       iso9660
 
    Boot sector type:  Unknown
 
    Boot sector info: 
 
    Operating System:  
 
    Boot files:        /boot/grub/grub.cfg
 

 
 

 
 
================================ 4 OS detected =================================
 

 
 
OS#1:   Ubuntu 22.04.2 LTS on sda12
 
OS#2:   Linux Mint 21.1 Vera (21.1) on sda6
 
OS#3:   Debian GNU/Linux 11 (bullseye) on sda9
 
OS#4:   Windows 8 or 10 on sda4
 

 
 
================================ Host/Hardware =================================
 

 
 
CPU architecture: 64-bit
 
Video: Haswell-ULT Integrated Graphics Controller from Intel Corporation
 
Live-session OS is Ubuntu 64-bit (Boot-Repair-Disk 64bit 20200604, bionic, x86_64)
 

 
 
===================================== UEFI =====================================
 

 
 
BIOS/UEFI firmware: 9ACN32WW from LENOVO
 
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
 
SecureBoot disabled (confirmed by mokutil).
 
BootCurrent: 0002
 
Timeout: 2 seconds
 
BootOrder: 0004,0003,0005,2001,2003,2002
 
Boot0000* EFI Network 0 for IPv4 (68-F7-28-0E-D2-48)  PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(68f7280ed248,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
 
Boot0001* EFI Network 0 for IPv6 (68-F7-28-0E-D2-48)  PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(68f7280ed248,0)/IPv6([::]:<->[::]:,0,0)RC
 
Boot0002* EFI USB Device (SD/MMC  Card  Reader) PciRoot(0x0)/Pci(0x1d,0x0)/USB(0,0)/USB(0,0)/HD(1,MBR,0x2c534026,0x3c4,0x1340)RC
 
Boot0003* ubuntu HD(2,GPT,06469d0d-bccd-429a-b29e-c02d22337394,0x96800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
 
Boot0004* debian HD(2,GPT,06469d0d-bccd-429a-b29e-c02d22337394,0x96800,0x32000)/File(\EFI\debian\shimx64.efi)
 
Boot0005* Windows Boot Manager HD(2,GPT,06469d0d-bccd-429a-b29e-c02d22337394,0x96800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
 
Boot0008* EFI Network 0 for IPv4 (68-F7-28-0E-D2-48)  PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(68f7280ed248,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
 
Boot0009* EFI Network 0 for IPv6 (68-F7-28-0E-D2-48)  PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(68f7280ed248,0)/IPv6([::]:<->[::]:,0,0)RC
 
Boot000A* EFI Network 0 for IPv6 (68-F7-28-0E-D2-48)  PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(68f7280ed248,0)/IPv6([::]:<->[::]:,0,0)RC
 
Boot000D* EFI Network 0 for IPv4 (68-F7-28-0E-D2-48)  PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(68f7280ed248,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
 
Boot000E* EFI Network 0 for IPv6 (68-F7-28-0E-D2-48)  PciRoot(0x0)/Pci(0x1c,0x0)/Pci(0x0,0x0)/MAC(68f7280ed248,0)/IPv6([::]:<->[::]:,0,0)RC
 
Boot2001* EFI USB Device RC
 
Boot2002* EFI DVD/CDROM RC
 
Boot2003* EFI Network RC
 

 
 
64349b3622c65f495a99dbf6102496e3   sda2/Boot/bootx64.efi
 
e06a4832fa56a95819cdb62360d8e95f   sda2/Boot/fbia32.efi
 
a9c517741ac31962d7feb152948ad1ee   sda2/Boot/fbx64.efi
 
a660182adef313615746a665966d2ccc   sda2/Boot/mmx64.efi
 
99d0f360409aef39f4eb55b4d6d11b08   sda2/debian/fbx64.efi
 
8af5de47338c2010714ee8dbd7bc5c2f   sda2/debian/grubx64.efi
 
e6efb5c12f230c5c0c33c5c77d67ad2f   sda2/debian/mmx64.efi
 
f7620ab72c3d481f1a02daf84ef54e1d   sda2/debian/shimx64.efi
 
5ddf997e8b025bfbc2009e85b32f60dc   sda2/ubuntu/grubx64.efi
 
a660182adef313615746a665966d2ccc   sda2/ubuntu/mmx64.efi
 
64349b3622c65f495a99dbf6102496e3   sda2/ubuntu/shimx64.efi
 
4f0248591a11d5432380ba65f683879b   sda2/Microsoft/Boot/bootmgfw.efi
 
1feb5f9427494e6f598603caa3af7d99   sda2/Microsoft/Boot/bootmgr.efi
 
fecc659c3253ac65326801d790718171   sda2/Boot/BOOTIA32.efi
 

 
 
============================= Drive/Partition Info =============================
 

 
 
Disks info: ____________________________________________________________________
 

 
 
sda  : is-GPT, no-BIOSboot, has---ESP, not-usb, not-mmc, has-os, has-win, 2048 sectors * 512 bytes
 

 
 
Partitions info (1/3): _________________________________________________________
 

 
 
sda1  : no-os, 64, nopakmgr, no-docgrub, nogrub, nogrubinstall, no-grubenv, noupdategrub, not-far
 
sda10  : no-os, 64, nopakmgr, no-docgrub, nogrub, nogrubinstall, no-grubenv, noupdategrub, farbios
 
sda12  : is-os, 64, apt-get, signed grub-pc grub-efi ,  grub2, grub-install, grubenv-ok, update-grub, farbios
 
sda13  : no-os, 64, nopakmgr, no-docgrub, nogrub, nogrubinstall, no-grubenv, noupdategrub, farbios
 
sda2  : no-os, 64, nopakmgr, no-docgrub, nogrub, nogrubinstall, no-grubenv, noupdategrub, not-far
 
sda4  : is-os, 64, nopakmgr, no-docgrub, nogrub, nogrubinstall, no-grubenv, noupdategrub, farbios
 
sda5  : no-os, 64, nopakmgr, no-docgrub, nogrub, nogrubinstall, no-grubenv, noupdategrub, farbios
 
sda6  : is-os, 64, apt-get, signed grub-efi , grub2, grub-install, grubenv-ok, update-grub, farbios
 
sda7  : no-os, 64, nopakmgr, no-docgrub, nogrub, nogrubinstall, no-grubenv, noupdategrub, farbios
 
sda9  : is-os, 64, apt-get, signed grub-efi , grub2, grub-install, grubenv-ok, update-grub, farbios
 

 
 
Partitions info (2/3): _________________________________________________________
 

 
 
sda1  : isnotESP, part-has-no-fstab, no-nt, no-winload, recovery-or-hidden, no-bmgr, notwinboot
 
sda10  : isnotESP, part-has-no-fstab, no-nt, no-winload, no-recov-nor-hid, no-bmgr, notwinboot
 
sda12  : isnotESP, fstab-has-goodEFI, no-nt, no-winload, no-recov-nor-hid, no-bmgr, notwinboot
 
sda13  : isnotESP, part-has-no-fstab, no-nt, no-winload, no-recov-nor-hid, no-bmgr, notwinboot
 
sda2  : is---ESP, part-has-no-fstab, no-nt, no-winload, no-recov-nor-hid, no-bmgr, notwinboot
 
sda4  : isnotESP, part-has-no-fstab, no-nt, haswinload, no-recov-nor-hid, bootmgr, notwinboot
 
sda5  : isnotESP, part-has-no-fstab, no-nt, no-winload, recovery-or-hidden, no-bmgr, notwinboot
 
sda6  : isnotESP, fstab-has-goodEFI, no-nt, no-winload, no-recov-nor-hid, no-bmgr, notwinboot
 
sda7  : isnotESP, part-has-no-fstab, no-nt, no-winload, no-recov-nor-hid, no-bmgr, notwinboot
 
sda9  : isnotESP, fstab-has-goodEFI, no-nt, no-winload, recovery-or-hidden, no-bmgr, notwinboot
 

 
 
Partitions info (3/3): _________________________________________________________
 

 
 
sda1  : not--sepboot, no---boot, part-has-no-fstab, not-sep-usr, no---usr, part-has-no-fstab, no--grub.d, sda
 
sda10  : maybesepboot, no---boot, part-has-no-fstab, not-sep-usr, no---usr, part-has-no-fstab, no--grub.d, sda
 
sda12  : not--sepboot, with-boot, fstab-without-boot, not-sep-usr, with--usr, fstab-without-usr, std-grub.d, sda
 
sda13  : maybesepboot, no---boot, part-has-no-fstab, not-sep-usr, no---usr, part-has-no-fstab, no--grub.d, sda
 
sda2  : not--sepboot, no---boot, part-has-no-fstab, not-sep-usr, no---usr, part-has-no-fstab, no--grub.d, sda
 
sda4  : not--sepboot, no---boot, part-has-no-fstab, not-sep-usr, no---usr, part-has-no-fstab, no--grub.d, sda
 
sda5  : not--sepboot, no---boot, part-has-no-fstab, not-sep-usr, no---usr, part-has-no-fstab, no--grub.d, sda
 
sda6  : not--sepboot, with-boot, fstab-without-boot, not-sep-usr, with--usr, fstab-without-usr, std-grub.d, sda
 
sda7  : maybesepboot, no---boot, part-has-no-fstab, not-sep-usr, no---usr, part-has-no-fstab, no--grub.d, sda
 
sda9  : not--sepboot, with-boot, fstab-without-boot, not-sep-usr, with--usr, fstab-without-usr, std-grub.d, sda
 

 
 
fdisk -l (filtered): ___________________________________________________________
 

 
 
Disk sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
 
Disk identifier: E3720052-5FEE-4C5F-965B-C0BEBB805204
 
           Start        End    Sectors   Size Type
 
sda1        2048     616447     614400   300M Windows recovery environment
 
sda2      616448     821247     204800   100M EFI System
 
sda3      821248    1083391     262144   128M Microsoft reserved
 
sda4     1083392 1239528435 1238445044 590.5G Microsoft basic data
 
sda5  1239529472 1240819711    1290240   630M Windows recovery environment
 
sda6  1240819712 1318944767   78125056  37.3G Linux filesystem
 
sda7  1318944768 1436131327  117186560  55.9G Linux filesystem
 
sda8  1436131328 1451755519   15624192   7.5G Linux swap
 
sda9  1451755520 1543915519   92160000    44G Linux filesystem
 
sda10 1543915520 1677035519  133120000  63.5G Linux filesystem
 
sda11 1677035520 1697515519   20480000   9.8G Linux swap
 
sda12 1697515520 1785405439   87889920  41.9G Linux filesystem
 
sda13 1785405440 1933842431  148436992  70.8G Linux filesystem
 
sda14 1933842432 1953523711   19681280   9.4G Linux swap
 
Disk sdb: 3.8 GiB, 4075290624 bytes, 7959552 sectors
 
Disk identifier: 0x2c534026
 
      Boot Start     End Sectors  Size Id Type
 
sdb1  *        0 1802239 1802240  880M  0 Empty
 
sdb2         964    5891    4928  2.4M ef EFI (FAT-12/16/32)
 
Disk zram0: 981.7 MiB, 1029337088 bytes, 251303 sectors
 
Disk zram1: 981.7 MiB, 1029337088 bytes, 251303 sectors
 
Disk zram2: 981.7 MiB, 1029337088 bytes, 251303 sectors
 
Disk zram3: 981.7 MiB, 1029337088 bytes, 251303 sectors
 

 
 
parted -lm (filtered): _________________________________________________________
 

 
 
sda:1000GB:scsi:512:4096:gpt:ATA ST1000LM024 HN-M:;
 
1:1049kB:316MB:315MB:ntfs:Basic data partition:hidden, diag;
 
2:316MB:420MB:105MB:fat32:EFI System Partition:boot, esp;
 
3:420MB:555MB:134MB::Microsoft reserved partition:msftres;
 
4:555MB:635GB:634GB:ntfs:Basic data partition:msftdata;
 
5:635GB:635GB:661MB:ntfs::hidden, diag;
 
6:635GB:675GB:40.0GB:ext4::;
 
7:675GB:735GB:60.0GB:ext4::;
 
8:735GB:743GB:8000MB:linux-swap(v1)::;
 
9:743GB:790GB:47.2GB:ext4::hidden;
 
10:790GB:859GB:68.2GB:ext4::;
 
11:859GB:869GB:10.5GB:linux-swap(v1)::;
 
12:869GB:914GB:45.0GB:ext4::;
 
13:914GB:990GB:76.0GB:ext4::;
 
14:990GB:1000GB:10.1GB:linux-swap(v1)::;
 
sdb:4075MB:scsi:512:512:msdos:SD/MMC Card Reader:;
 
2:494kB:3017kB:2523kB:::esp;
 

 
 
Free space >10MiB: ______________________________________________________________
 

 
 
sdb: 2.88MiB:3886MiB:3884MiB
 

 
 
blkid (filtered): ______________________________________________________________
 

 
 
NAME    FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL
 
sda                                                                                                               
 
&#9500;&#9472;sda1  ntfs     3AAA1922AA18DC67                     6e48f75e-cbe2-404e-8819-e96ba66a89c5 Recovery               Basic data partition
 
&#9500;&#9472;sda2  vfat     361A-46ED                            06469d0d-bccd-429a-b29e-c02d22337394                        EFI System Partition
 
&#9500;&#9472;sda3                                                92e4c3b2-658c-42c6-90fc-bcf0a41a8d78                        Microsoft reserved partition
 
&#9500;&#9472;sda4  ntfs     EEA61CC6A61C9167                     2041195a-89ff-4d1e-95b0-72353df77d03                        Basic data partition
 
&#9500;&#9472;sda5  ntfs     7E6A31F06A31A635                     81734a7a-d7c8-4aee-bbc3-70de31c44d0e                        
 
&#9500;&#9472;sda6  ext4     da124555-b9f0-45c9-8a4e-886eefcf6e42 abd6e512-df52-4ed8-b191-0eca90f40655 Linux Mint             
 
&#9500;&#9472;sda7  ext4     41530e61-f699-4f46-819f-e5f794671ff8 d813f8ae-f365-471f-b67d-604a727fb2e7 LinuxMint Home         
 
&#9500;&#9472;sda8  swap     780e3322-d08b-4c65-bb64-8d56ea523f6c 1484460d-d1f6-4144-9c4c-d2d8ac8f268e                        
 
&#9500;&#9472;sda9  ext4     7fcb4e5e-43c7-4fa0-9e01-dec08d1a46ab bccb94f6-237a-fc4a-b23b-dd1c2ef11615                        
 
&#9500;&#9472;sda10 ext4     dd956e21-0e60-4729-a608-fa64fece073f a1657fc7-f059-1a4c-9765-8b7640b95ab9                        
 
&#9500;&#9472;sda11 swap     43e5cefb-f476-49b9-93de-af3fa388ecd8 b52d78c7-679a-a443-89a6-494760dc0482                        
 
&#9500;&#9472;sda12 ext4     73e502d0-098e-4e03-9f7c-fdb802936d6f 0e245cbd-a3a8-4a88-90f7-ad1d6cb8bf6a                        
 
&#9500;&#9472;sda13 ext4     ace1ee9a-4d9f-4181-aa33-ebb732256dad 4ea9ffc2-9480-452b-b4cf-eea083af9d1a                        
 
&#9492;&#9472;sda14 swap     dafa167e-6a2e-4137-8309-f16bf3710641 754c3474-8069-4565-bb01-c2a98dd8df57                        
 
sdb     iso9660  2020-06-13-00-42-55-00                                                    Boot-Repair-Disk 64bit 
 
&#9500;&#9472;sdb1  iso9660  2020-06-13-00-42-55-00               2c534026-01                          Boot-Repair-Disk 64bit 
 
&#9492;&#9472;sdb2  vfat     D055-8513                            2c534026-02                          Boot-Repair-Disk 64bit 
 

 
 
Mount points (filtered): _______________________________________________________
 

 
 
             Avail Use% Mounted on
 
/dev/sda1   288.6M   4% /mnt/boot-sav/sda1
 
/dev/sda10   55.6G   5% /mnt/boot-sav/sda10
 
/dev/sda12   24.5G  35% /mnt/boot-sav/sda12
 
/dev/sda13   34.4G  45% /mnt/boot-sav/sda13
 
/dev/sda2    55.1M  43% /mnt/boot-sav/sda2
 
/dev/sda4   507.6G  14% /mnt/boot-sav/sda4
 
/dev/sda5    86.5M  86% /mnt/boot-sav/sda5
 
/dev/sda6    13.8G  62% /mnt/boot-sav/sda6
 
/dev/sda7    50.3G   3% /mnt/boot-sav/sda7
 
/dev/sda9    26.1G  34% /mnt/boot-sav/sda9
 
/dev/sdb         0 100% /cdrom
 

 
 
Mount options (filtered): ______________________________________________________
 

 
 

 
 
===================== sda2/efi/debian/grub.cfg (filtered) ======================
 

 
 
search.fs_uuid 7fcb4e5e-43c7-4fa0-9e01-dec08d1a46ab root hd0,gpt9 
 
set prefix=($root)'/boot/grub'
 
configfile $prefix/grub.cfg
 

 
 
===================== sda2/efi/ubuntu/grub.cfg (filtered) ======================
 

 
 
search.fs_uuid 73e502d0-098e-4e03-9f7c-fdb802936d6f root hd0,gpt12 
 
set prefix=($root)'/boot/grub'
 
configfile $prefix/grub.cfg
 

 
 
====================== sda6/boot/grub/grub.cfg (filtered) ======================
 

 
 
Linux Mint 21.1 Cinnamon   da124555-b9f0-45c9-8a4e-886eefcf6e42
 
Linux Mint 21.1 Cinnamon, with Linux 5.15.0-75-generic   da124555-b9f0-45c9-8a4e-886eefcf6e42
 
Linux Mint 21.1 Cinnamon, with Linux 5.15.0-69-generic   da124555-b9f0-45c9-8a4e-886eefcf6e42
 
Ubuntu 22.04.2 LTS (22.04) (on sda12)   73e502d0-098e-4e03-9f7c-fdb802936d6f
 
Ubuntu (on sda12)   73e502d0-098e-4e03-9f7c-fdb802936d6f
 
Ubuntu, with Linux 5.19.0-43-generic (on sda12)   73e502d0-098e-4e03-9f7c-fdb802936d6f
 
Ubuntu, with Linux 5.19.0-42-generic (on sda12)   73e502d0-098e-4e03-9f7c-fdb802936d6f
 
Ubuntu, with Linux 5.15.0-73-generic (on sda12)   73e502d0-098e-4e03-9f7c-fdb802936d6f
 
Windows Boot Manager (on sda2)   osprober-efi-361A-46ED
 
Debian GNU/Linux 11 (bullseye) (on sda9)   7fcb4e5e-43c7-4fa0-9e01-dec08d1a46ab
 
Debian GNU/Linux (on sda9)   7fcb4e5e-43c7-4fa0-9e01-dec08d1a46ab
 
Debian GNU/Linux, with Linux 5.10.0-21-amd64 (on sda9)   7fcb4e5e-43c7-4fa0-9e01-dec08d1a46ab
 
Debian GNU/Linux, with Linux 5.10.0-19-amd64 (on sda9)   7fcb4e5e-43c7-4fa0-9e01-dec08d1a46ab
 
Debian GNU/Linux, with Linux 5.10.0-9-amd64 (on sda9)   7fcb4e5e-43c7-4fa0-9e01-dec08d1a46ab
 
### END /etc/grub.d/30_os-prober ###
 
UEFI Firmware Settings   uefi-firmware
 
### END /etc/grub.d/30_uefi-firmware ###
 

 
 
========================== sda6/etc/fstab (filtered) ===========================
 

 
 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
 
# / was on /dev/sda6 during installation
 
UUID=da124555-b9f0-45c9-8a4e-886eefcf6e42 /               ext4    errors=remount-ro 0       1
 
# /boot/efi was on /dev/sda2 during installation
 
UUID=361A-46ED  /boot/efi       vfat    umask=0077      0       1
 
# /home was on /dev/sda7 during installation
 
UUID=41530e61-f699-4f46-819f-e5f794671ff8 /home           ext4    defaults        0       2
 
# swap was on /dev/sda8 during installation
 
UUID=597c755a-f90a-46d7-be4d-8e9466164b2d none            swap    sw              0       0
 
//192.168.1.1/linksys02275/new%20volume
 

 
 
======================= sda6/etc/default/grub (filtered) =======================
 

 
 
GRUB_DEFAULT=0
 
GRUB_TIMEOUT_STYLE=hidden
 
GRUB_TIMEOUT=10
 
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 
GRUB_CMDLINE_LINUX=""
 

 
 
==================== sda6: Location of files loaded by Grub ====================
 

 
 
           GiB - GB             File                                 Fragment(s)
 
 616.432903290 = 661.889789952  boot/grub/grub.cfg                             1
 
 612.648487091 = 657.826304000  boot/vmlinuz                                   1
 
 594.679718018 = 638.532485120  boot/vmlinuz-5.15.0-69-generic                 2
 
 612.648487091 = 657.826304000  boot/vmlinuz-5.15.0-75-generic                 1
 
 594.679718018 = 638.532485120  boot/vmlinuz.old                               2
 
 593.637378693 = 637.413281792  boot/initrd.img                                2
 
 619.371738434 = 665.045340160  boot/initrd.img-5.15.0-69-generic              2
 
 593.637378693 = 637.413281792  boot/initrd.img-5.15.0-75-generic              2
 
 619.371738434 = 665.045340160  boot/initrd.img.old                            2
 

 
 
===================== sda6: ls -l /etc/grub.d/ (filtered) ======================
 

 
 
-rwxr-xr-x 1 root root 18683 Dec  2  2022 10_linux
 
-rwxr-xr-x 1 root root 43031 Dec  2  2022 10_linux_zfs
 
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
 
-rwxr-xr-x 1 root root 13369 Dec  2  2022 30_os-prober
 
-rwxr-xr-x 1 root root  1372 Dec  2  2022 30_uefi-firmware
 
-rwxr-xr-x 1 root root   700 Jul  3  2022 35_fwupd
 
-rwxr-xr-x 1 root root   214 Mar  4  2018 40_custom
 
-rwxr-xr-x 1 root root   215 Dec  2  2022 41_custom
 

 
 
====================== sda9/boot/grub/grub.cfg (filtered) ======================
 

 
 
Debian GNU/Linux   7fcb4e5e-43c7-4fa0-9e01-dec08d1a46ab
 
Debian GNU/Linux, with Linux 5.10.0-21-amd64   7fcb4e5e-43c7-4fa0-9e01-dec08d1a46ab
 
Debian GNU/Linux, with Linux 5.10.0-19-amd64   7fcb4e5e-43c7-4fa0-9e01-dec08d1a46ab
 
Debian GNU/Linux, with Linux 5.10.0-9-amd64   7fcb4e5e-43c7-4fa0-9e01-dec08d1a46ab
 
Ubuntu 22.04.2 LTS (22.04) (on sda12)   73e502d0-098e-4e03-9f7c-fdb802936d6f
 
Ubuntu (on sda12)   73e502d0-098e-4e03-9f7c-fdb802936d6f
 
Ubuntu, with Linux 5.19.0-41-generic (on sda12)   73e502d0-098e-4e03-9f7c-fdb802936d6f
 
Ubuntu, with Linux 5.19.0-40-generic (on sda12)   73e502d0-098e-4e03-9f7c-fdb802936d6f
 
Ubuntu, with Linux 5.15.0-72-generic (on sda12)   73e502d0-098e-4e03-9f7c-fdb802936d6f
 
Ubuntu, with Linux 5.15.0-71-generic (on sda12)   73e502d0-098e-4e03-9f7c-fdb802936d6f
 
Windows Boot Manager (on sda2)   osprober-efi-361A-46ED
 
Linux Mint 21.1 Vera (21.1) (on sda6)   da124555-b9f0-45c9-8a4e-886eefcf6e42
 
Linux Mint 21.1 Cinnamon (on sda6)   da124555-b9f0-45c9-8a4e-886eefcf6e42
 
Linux Mint 21.1 Cinnamon, with Linux 5.15.0-69-generic (on sda6)   da124555-b9f0-45c9-8a4e-886eefcf6e42
 
Linux Mint 21.1 Cinnamon, with Linux 5.15.0-67-generic (on sda6)   da124555-b9f0-45c9-8a4e-886eefcf6e42
 
### END /etc/grub.d/30_os-prober ###
 
UEFI Firmware Settings   uefi-firmware
 
### END /etc/grub.d/30_uefi-firmware ###
 

 
 
========================== sda9/etc/fstab (filtered) ===========================
 

 
 
# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
 
UUID=361A-46ED                            /boot/efi      vfat    defaults,noatime 0 2
 
UUID=7fcb4e5e-43c7-4fa0-9e01-dec08d1a46ab /              ext4    defaults,noatime 0 1
 
UUID=dd956e21-0e60-4729-a608-fa64fece073f /home          ext4    defaults,noatime 0 2
 
UUID=43e5cefb-f476-49b9-93de-af3fa388ecd8 swap           swap    defaults,noatime 0 0
 

 
 
======================= sda9/etc/default/grub (filtered) =======================
 

 
 
GRUB_DEFAULT=0
 
GRUB_TIMEOUT=5
 
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash resume=UUID=43e5cefb-f476-49b9-93de-af3fa388ecd8"
 
GRUB_CMDLINE_LINUX=""
 

 
 
==================== sda9: Location of files loaded by Grub ====================
 

 
 
           GiB - GB             File                                 Fragment(s)
 
 723.377216339 = 776.720371712  boot/grub/grub.cfg                             1
 
 715.683242798 = 768.459030528  boot/vmlinuz-5.10.0-19-amd64                   1
 
 721.730167389 = 774.951866368  boot/vmlinuz-5.10.0-21-amd64                   1
 
 724.382564545 = 777.799856128  boot/vmlinuz-5.10.0-9-amd64                    1
 
 721.730167389 = 774.951866368  vmlinuz                                        1
 
 715.683242798 = 768.459030528  vmlinuz.old                                    1
 
 716.063907623 = 768.867766272  boot/initrd.img-5.10.0-19-amd64                1
 
 727.643810272 = 781.301592064  boot/initrd.img-5.10.0-21-amd64                1
 
 695.445232391 = 746.728632320  boot/initrd.img-5.10.0-9-amd64                 1
 
 727.643810272 = 781.301592064  initrd.img                                     1
 
 716.063907623 = 768.867766272  initrd.img.old                                 1
 

 
 
===================== sda9: ls -l /etc/grub.d/ (filtered) ======================
 

 
 
-rwxr-xr-x 1 root root 14123 Aug  1  2022 10_linux
 
-rwxr-xr-x 1 root root 14180 Aug  1  2022 20_linux_xen
 
-rwxr-xr-x 1 root root 12910 Aug  1  2022 30_os-prober
 
-rwxr-xr-x 1 root root  1372 Aug  1  2022 30_uefi-firmware
 
-rwxr-xr-x 1 root root   214 Jul 10  2021 40_custom
 
-rwxr-xr-x 1 root root   215 Aug  1  2022 41_custom
 

 
 
===================== sda12/boot/grub/grub.cfg (filtered) ======================
 

 
 
Ubuntu   73e502d0-098e-4e03-9f7c-fdb802936d6f
 
Ubuntu, with Linux 5.19.0-43-generic   73e502d0-098e-4e03-9f7c-fdb802936d6f
 
Ubuntu, with Linux 5.19.0-42-generic   73e502d0-098e-4e03-9f7c-fdb802936d6f
 
Ubuntu, with Linux 5.15.0-73-generic   73e502d0-098e-4e03-9f7c-fdb802936d6f
 
Windows Boot Manager (on sda2)   osprober-efi-361A-46ED
 
Linux Mint 21.1 Vera (21.1) (on sda6)   da124555-b9f0-45c9-8a4e-886eefcf6e42
 
Linux Mint 21.1 Cinnamon (on sda6)   da124555-b9f0-45c9-8a4e-886eefcf6e42
 
Linux Mint 21.1 Cinnamon, with Linux 5.15.0-72-generic (on sda6)   da124555-b9f0-45c9-8a4e-886eefcf6e42
 
Linux Mint 21.1 Cinnamon, with Linux 5.15.0-69-generic (on sda6)   da124555-b9f0-45c9-8a4e-886eefcf6e42
 
Debian GNU/Linux 11 (bullseye) (on sda9)   7fcb4e5e-43c7-4fa0-9e01-dec08d1a46ab
 
Debian GNU/Linux (on sda9)   7fcb4e5e-43c7-4fa0-9e01-dec08d1a46ab
 
Debian GNU/Linux, with Linux 5.10.0-21-amd64 (on sda9)   7fcb4e5e-43c7-4fa0-9e01-dec08d1a46ab
 
Debian GNU/Linux, with Linux 5.10.0-19-amd64 (on sda9)   7fcb4e5e-43c7-4fa0-9e01-dec08d1a46ab
 
Debian GNU/Linux, with Linux 5.10.0-9-amd64 (on sda9)   7fcb4e5e-43c7-4fa0-9e01-dec08d1a46ab
 
### END /etc/grub.d/30_os-prober ###
 
UEFI Firmware Settings   uefi-firmware
 
### END /etc/grub.d/30_uefi-firmware ###
 

 
 
========================== sda12/etc/fstab (filtered) ==========================
 

 
 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
 
# / was on /dev/sda12 during installation
 
UUID=73e502d0-098e-4e03-9f7c-fdb802936d6f /               ext4    errors=remount-ro 0       1
 
# /boot/efi was on /dev/sda2 during installation
 
UUID=361A-46ED  /boot/efi       vfat    umask=0077      0       1
 
# /home was on /dev/sda13 during installation
 
UUID=ace1ee9a-4d9f-4181-aa33-ebb732256dad /home           ext4    defaults        0       2
 
# swap was on /dev/sda11 during installation
 
UUID=43e5cefb-f476-49b9-93de-af3fa388ecd8 none            swap    sw              0       0
 
# swap was on /dev/sda14 during installation
 
UUID=dafa167e-6a2e-4137-8309-f16bf3710641 none            swap    sw              0       0
 
# swap was on /dev/sda8 during installation
 
UUID=780e3322-d08b-4c65-bb64-8d56ea523f6c none            swap    sw              0       0
 

 
 
====================== sda12/etc/default/grub (filtered) =======================
 

 
 
GRUB_DEFAULT=0
 
GRUB_TIMEOUT_STYLE=hidden
 
GRUB_TIMEOUT=10
 
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 
GRUB_CMDLINE_LINUX=""
 

 
 
=================== sda12: Location of files loaded by Grub ====================
 

 
 
           GiB - GB             File                                 Fragment(s)
 
 822.355178833 = 882.997149696  boot/grub/grub.cfg                             1
 
 813.105503082 = 873.065385984  boot/vmlinuz                                   2
 
 813.105503082 = 873.065385984  boot/vmlinuz-5.15.0-73-generic                 2
 
 820.652961731 = 881.169408000  boot/vmlinuz-5.19.0-42-generic                 1
 
 814.270149231 = 874.315915264  boot/vmlinuz-5.19.0-43-generic                 2
 
 814.270149231 = 874.315915264  boot/vmlinuz.old                               2
 
 818.242668152 = 878.581374976  boot/initrd.img                                3
 
 818.242668152 = 878.581374976  boot/initrd.img-5.15.0-73-generic              3
 
 819.131576538 = 879.535833088  boot/initrd.img-5.19.0-42-generic              3
 
 844.170619965 = 906.421301248  boot/initrd.img-5.19.0-43-generic              1
 
 844.170619965 = 906.421301248  boot/initrd.img.old                            1
 

 
 
===================== sda12: ls -l /etc/grub.d/ (filtered) =====================
 

 
 
-rwxr-xr-x 1 root root 18683 Apr 15  2022 10_linux
 
-rwxr-xr-x 1 root root 43031 Apr 15  2022 10_linux_zfs
 
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
 
-rwxr-xr-x 1 root root 13369 Apr 15  2022 30_os-prober
 
-rwxr-xr-x 1 root root  1372 Apr 15  2022 30_uefi-firmware
 
-rwxr-xr-x 1 root root   700 Feb 21  2022 35_fwupd
 
-rwxr-xr-x 1 root root   214 Aug 12  2021 40_custom
 
-rwxr-xr-x 1 root root   215 Apr 15  2022 41_custom
 

 
 
====================== sdb/boot/grub/grub.cfg (filtered) =======================
 

 
 
Boot-Repair-Disk session
 
Boot-Repair-Disk session (failsafe)
 

 
 
==================== sdb: Location of files loaded by Grub =====================
 

 
 
           GiB - GB             File                                 Fragment(s)
 
            ?? = ??             boot/grub/grub.cfg                             1
 

 
 

 
 

 
 
Suggested repair: ______________________________________________________________
 

 
 
The default repair of the Boot-Repair utility would reinstall the grub-efi of
 
sda12,
 
using the following options:  sda2/boot/efi
 
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file
 

 
 
Final advice in case of suggested repair: ______________________________________
 

 
 
Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.2 LTS entry (sda2/efi/****/grub****.efi (**** will be updated in the final message) file) !
 
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
 
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
 
For example you can boot into Windows, then type the following command in an admin command prompt:
 
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)
```

---

### Post by oldfred on 2023-06-19
Please use Code tags for any terminal or text output, easy to add with Forum's Go Advanced editor & # icon.
With Boot-Repair better to just post link as it is then easier to review in another tab.

Your grub menu updates are out of sync. Perhaps an update to grub menu will resolve issue.
Ubuntu only keeps 2 kernels, but the grub you are booting from is using one of the deleted kernels not one of the newer ones.

With multiple installs better to create your own boot stanza's in 40_custom and use the link to the newest kernel.
Ubuntu always keeps a link in /boot to latest kernel and you can use that as a permanent boot.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Configfile example to another grub.cfg
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

### Post by tjharring on 2023-06-20
> **oldfred said:**
> Please use Code tags for any terminal or text output, easy to add with Forum's Go Advanced editor & # icon.
With Boot-Repair better to just post link as it is then easier to review in another tab.

Your grub menu updates are out of sync. Perhaps an update to grub menu will resolve issue.
Ubuntu only keeps 2 kernels, but the grub you are booting from is using one of the deleted kernels not one of the newer ones.

With multiple installs better to create your own boot stanza's in 40_custom and use the link to the newest kernel.
Ubuntu always keeps a link in /boot to latest kernel and you can use that as a permanent boot.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Configfile example to another grub.cfg
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

I tried to update grub but had the same error. Here is the link to the boot configuration, 
paste.ubuntu.com/p/3jFjVm3W3q/

Hopefully this will help.

---

### Post by oldfred on 2023-06-20
You did not post a clickable link.
And I tried to add the https:// to it and it still says invalid.
Please rerun report and post a link that works.

---

### Post by tjharring on 2023-06-21
> **oldfred said:**
> You did not post a clickable link.
And I tried to add the https:// to it and it still says invalid.
Please rerun report and post a link that works.

The first time I ran the report and tried to go to the URL it produced it brought me to a dead page. That's why I re-ran the report saved local and copy and pasted the text previously. It also struck me that the address the software gave was http:// instead of https.
I will run it again tonight and post the link.

---

### Post by tjharring on 2023-06-21
> **oldfred said:**
> You did not post a clickable link.
And I tried to add the https:// to it and it still says invalid.
Please rerun report and post a link that works.

Ok let's try this one more time. Here is the link provided by boot repair. [http://paste.ubuntu.com/p/XyP8rXg8YT/](http://paste.ubuntu.com/p/XyP8rXg8YT/)

---

### Post by oldfred on 2023-06-21
the only place 5.19.0-41-generic is referred to, is in Debian's menu.
Ubuntu has been updated to have -42 & -43. When new kernel installed in Ubuntu, it keeps two and deletes the oldest. So from Debian you are trying to boot a now deleted kernel.
You can update Debian's grub menu to be correct. Now sure if it uses os-prober. With grub 2.06 they are recommending you turn off os-prober in grub's settings.

You should be able to boot Ubuntu directly from UEFI boot menu.
But since you also have Mint, even though not an official flavor of Ubuntu, it uses ubuntu in UEFI boot entry. So depending on whether Ubuntu or Mint has last done a major grub update, the ubuntu entry in UEFI may boot one or the other.

With multiple installs, best to turn off os-prober & add your own boot stanza into 40_custom, at least for Ubuntu. Ubuntu updates a link in /boot to most recent kernel. (line 813).  So easy to add a simple boot stanza to 40_custom to always boot most current kernel without having to update grub menu.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Configfile example to another grub.cfg
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

### Post by tjharring on 2023-06-21
> **oldfred said:**
> the only place 5.19.0-41-generic is referred to, is in Debian's menu.
Ubuntu has been updated to have -42 & -43. When new kernel installed in Ubuntu, it keeps two and deletes the oldest. So from Debian you are trying to boot a now deleted kernel.
You can update Debian's grub menu to be correct. Now sure if it uses os-prober. With grub 2.06 they are recommending you turn off os-prober in grub's settings.

You should be able to boot Ubuntu directly from UEFI boot menu.
But since you also have Mint, even though not an official flavor of Ubuntu, it uses ubuntu in UEFI boot entry. So depending on whether Ubuntu or Mint has last done a major grub update, the ubuntu entry in UEFI may boot one or the other.

With multiple installs, best to turn off os-prober & add your own boot stanza into 40_custom, at least for Ubuntu. Ubuntu updates a link in /boot to most recent kernel. (line 813).  So easy to add a simple boot stanza to 40_custom to always boot most current kernel without having to update grub menu.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Configfile example to another grub.cfg
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

Oldfred running grub update with os prober off did the trick. I would like to thank you for the help.

---

