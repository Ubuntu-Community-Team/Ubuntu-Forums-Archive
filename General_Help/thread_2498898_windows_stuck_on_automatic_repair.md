---
title: "windows stuck on automatic repair"
date: 2024-07-02
forum: General Help
---

### Post by cheransankaran on 2024-07-02
```
boot-repair-4ppa2075                                              [20240702_1353]


============================== Boot Info Summary ===============================


 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => Windows is installed in the MBR of /dev/nvme1n1.


nvme0n1p1: _____________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


nvme0n1p2: _____________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


nvme0n1p3: _____________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  According to the info in the boot sector, nvme0n1p3 
                       starts at sector 29. But according to the info from 
                       fdisk, nvme0n1p3 starts at sector 32768. According to 
                       the info in the boot sector, nvme0n1p3 has 3906994175 
                       sectors, but according to the info from fdisk, it has 
                       3906996366 sectors.
    Operating System:  
    Boot files:        


nvme1n1p1: _____________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


nvme1n1p2: _____________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi


nvme1n1p3: _____________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


nvme1n1p4: _____________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


nvme1n1p5: _____________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe


nvme1n1p6: _____________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


nvme1n1p7: _____________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub




================================ 2 OS detected =================================


OS#1:   The OS currently in use - Ubuntu 22.04.4 LTS on nvme1n1p7
OS#2:   Windows 10 or 11 on nvme1n1p5


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: TU116 [GeForce GTX 1660] from NVIDIA Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-6.5.0-41-generic root=UUID=85f1e6c3-e8a6-4a94-b599-ec46ffb6e0ff ro quiet splash vt.handoff=7
df -Th / : /dev/nvme1n1p7 ext4  212G   15G  187G   8% /


===================================== UEFI =====================================


BIOS/UEFI firmware: F41(5.14) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0000,0002,0003
Boot0000* Windows Boot Manager	HD(2,GPT,5596dfd4-be3b-41b9-bfdb-a5587acc5a41,0x109000,0x31800)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...,................
Boot0001* ubuntu	HD(2,GPT,5596dfd4-be3b-41b9-bfdb-a5587acc5a41,0x109000,0x31800)/File(\EFI\ubuntu\shimx64.efi)
Boot0002* WDS500G3X0C-00SJG0	BBS(HD,,0x0)..BO
Boot0003* WD Blue SN570 2TB	BBS(HD,,0x0)..BO


64349b3622c65f495a99dbf6102496e3   nvme1n1p2/Boot/bkpbootx64.efi
64349b3622c65f495a99dbf6102496e3   nvme1n1p2/Boot/bootx64.efi
a9c517741ac31962d7feb152948ad1ee   nvme1n1p2/Boot/fbx64.efi
a660182adef313615746a665966d2ccc   nvme1n1p2/Boot/mmx64.efi
a1da253696a304dce6b4668b70151c0e   nvme1n1p2/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   nvme1n1p2/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   nvme1n1p2/ubuntu/shimx64.efi
df480f092e56b632513b4616bdeade95   nvme1n1p2/Microsoft/Boot/bootmgfw.efi
0a70ebdfe73694eb6188f70e81b47a79   nvme1n1p2/Microsoft/Boot/bootmgr.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


nvme1n1	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	has-win,	2048 sectors * 512 bytes
nvme0n1	: is-GPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, no-os,	no-wind,	34 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


nvme1n1p7	: is-os,	64, apt-get,	signed grub-pc grub-efi ,	grub2,	grub-install,	grubenv-ok,	update-grub,	end-after-100GB
nvme0n1p3	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB
nvme1n1p2	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
nvme1n1p5	: is-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB
nvme1n1p1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
nvme0n1p1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
nvme1n1p3	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
nvme1n1p6	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	end-after-100GB


Partitions info (2/3): _________________________________________________________


nvme1n1p7	: isnotESP,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
nvme0n1p3	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
nvme1n1p2	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
nvme1n1p5	: isnotESP,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	no-bmgr,	notwinboot
nvme1n1p1	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot
nvme0n1p1	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
nvme1n1p3	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
nvme1n1p6	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot


Partitions info (3/3): _________________________________________________________


nvme1n1p7	: not--sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	nvme1n1
nvme0n1p3	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1
nvme1n1p2	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme1n1
nvme1n1p5	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme1n1
nvme1n1p1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme1n1
nvme0n1p1	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1
nvme1n1p3	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme1n1
nvme1n1p6	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme1n1


fdisk -l (filtered): ___________________________________________________________


Disk nvme1n1: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 2C9B2CD9-70C0-4317-9401-63BFB0FD5882
             Start       End   Sectors   Size Type
nvme1n1p1      2048   1085439   1083392   529M Windows recovery environment
nvme1n1p2   1085440   1288191    202752    99M EFI System
nvme1n1p3   1288192   1290239      2048     1M Microsoft LDM metadata
nvme1n1p4   1290240   1320959     30720    15M Microsoft reserved
nvme1n1p5   1320960 523713844 522392885 249.1G Microsoft LDM data
nvme1n1p6 976773120 976773134        15   7.5K Microsoft LDM data
nvme1n1p7 523714560 976771071 453056512   216G Linux filesystem
Partition table entries are not in disk order.
Disk nvme0n1: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk identifier: BCBD51C8-AAFF-4396-8F3E-65B8B3515396
         Start        End    Sectors  Size Type
nvme0n1p1    34       2081       2048    1M Microsoft LDM metadata
nvme0n1p2  2082      32767      30686   15M Microsoft reserved
nvme0n1p3 32768 3907029134 3906996367  1.8T Microsoft LDM data


parted -lm (filtered): _________________________________________________________


nvme0n1:2000GB:nvme:512:512:gpt:WD Blue SN570 2TB:;
1:17.4kB:1066kB:1049kB::LDM metadata partition:;
2:1066kB:16.8MB:15.7MB::Microsoft reserved partition:msftres;
3:16.8MB:2000GB:2000GB:ntfs:LDM data partition:;
nvme1n1:500GB:nvme:512:512:gpt:WDS500G3X0C-00SJG0:;
1:1049kB:556MB:555MB:ntfs:Basic data partition:hidden, diag;
2:556MB:660MB:104MB:fat32:EFI system partition:boot, esp;
3:660MB:661MB:1049kB::LDM metadata partition:;
4:661MB:676MB:15.7MB::Microsoft reserved partition:msftres;
5:676MB:268GB:267GB:ntfs:LDM data partition:;
7:268GB:500GB:232GB:ext4::;
6:500GB:500GB:7680B::LDM data partition:;


blkid (filtered): ______________________________________________________________


NAME        FSTYPE   UUID                                 PARTUUID                             LABEL      PARTLABEL
nvme1n1                                                                                                   
&#9500;&#9472;nvme1n1p1 ntfs     B46C7F9C6C7F57D6                     dea3d201-734f-4432-952f-0a6bc42630d6            Basic data partition
&#9500;&#9472;nvme1n1p2 vfat     0873-17FF                            5596dfd4-be3b-41b9-bfdb-a5587acc5a41            EFI system partition
&#9500;&#9472;nvme1n1p3                                               f0766720-40f4-11ee-818c-087190d2fbd0            LDM metadata partition
&#9500;&#9472;nvme1n1p4                                               1a10cbe2-a537-46c3-96f3-cf8b78de1571            Microsoft reserved partition
&#9500;&#9472;nvme1n1p5 ntfs     B2EE740CEE73C75F                     f9553e71-9a8d-437c-ad7d-d6c4c16be1e8            LDM data partition
&#9500;&#9472;nvme1n1p6                                               f0766724-40f4-11ee-818c-087190d2fbd0            LDM data partition
&#9492;&#9472;nvme1n1p7 ext4     85f1e6c3-e8a6-4a94-b599-ec46ffb6e0ff 0009b00c-4a66-4ee7-860b-cae626017f98            
nvme0n1                                                                                                   
&#9500;&#9472;nvme0n1p1                                               78279f20-4124-11ee-818d-087190d2fbd0            LDM metadata partition
&#9500;&#9472;nvme0n1p2                                               58a63cc9-de22-489c-afc6-a65d0f366e9a            Microsoft reserved partition
&#9492;&#9472;nvme0n1p3 ntfs     7266A70F66A6D361                     78279f23-4124-11ee-818d-087190d2fbd0 New Volume LDM data partition


Mount points (filtered): _______________________________________________________


                                     Avail Use% Mounted on
/dev/nvme0n1p3                        1.4T  23% /mnt/boot-sav/nvme0n1p3
/dev/nvme1n1p1                       89.1M  83% /mnt/boot-sav/nvme1n1p1
/dev/nvme1n1p2                       62.9M  34% /mnt/boot-sav/nvme1n1p2
/dev/nvme1n1p5                      147.9G  41% /mnt/boot-sav/nvme1n1p5
/dev/nvme1n1p7                      186.2G   7% /
efivarfs                               99K  19% /sys/firmware/efi/efivars


Mount options (filtered): ______________________________________________________


/dev/nvme0n1p3                      fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/nvme1n1p1                      fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/nvme1n1p2                      vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/nvme1n1p5                      fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/nvme1n1p7                      ext4            rw,relatime,errors=remount-ro


=================== nvme1n1p2/efi/ubuntu/grub.cfg (filtered) ===================


search.fs_uuid 85f1e6c3-e8a6-4a94-b599-ec46ffb6e0ff root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


=================== nvme1n1p7/boot/grub/grub.cfg (filtered) ====================


Ubuntu   85f1e6c3-e8a6-4a94-b599-ec46ffb6e0ff
Windows Boot Manager (on nvme1n1p2)   osprober-efi-0873-17FF
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###


======================== nvme1n1p7/etc/fstab (filtered) ========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme1n1p7 during installation
UUID=85f1e6c3-e8a6-4a94-b599-ec46ffb6e0ff /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme1n1p2 during installation
UUID=0873-17FF  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0


==================== nvme1n1p7/etc/default/grub (filtered) =====================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false


================= nvme1n1p7: Location of files loaded by Grub ==================


           GiB - GB             File                                 Fragment(s)
 379.590496063 = 407.582191616  boot/grub/grub.cfg                             1
 371.942977905 = 399.370731520  boot/vmlinuz                                   2
 259.872623444 = 279.036104704  boot/vmlinuz-6.5.0-18-generic                  1
 371.942977905 = 399.370731520  boot/vmlinuz-6.5.0-41-generic                  2
 259.872623444 = 279.036104704  boot/vmlinuz.old                               1
 257.601558685 = 276.597567488  boot/initrd.img                                2
 303.874996185 = 326.283292672  boot/initrd.img-6.5.0-18-generic               6
 257.601558685 = 276.597567488  boot/initrd.img-6.5.0-41-generic               2
 303.874996185 = 326.283292672  boot/initrd.img.old                            6


=================== nvme1n1p7: ls -l /etc/grub.d/ (filtered) ===================


-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 17  2023 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom






Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would reinstall the grub-efi of
nvme1n1p7,
using the following options:  nvme1n1p2/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups


Final advice in case of suggested repair: ______________________________________


Please do not forget to make your UEFI firmware boot on the The OS currently in use - Ubuntu 22.04.4 LTS entry (nvme1n1p2/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)
```

any recomendations apriciated

---

### Post by tea for one on 2024-07-02
> windows stuck on automatic repair 
I am assuming that your Windows Boot Manager or Windows file system is corrupt.
Unfortunately, boot-repair will not fix Windows difficulties.

You will need to use Windows utilities via a Windows installation iso
Boot-repair will only be useful if Windows is in full working order.

---

### Post by oldfred on 2024-07-02
How did you ever get these?
Microsoft LDM metadata
Windows is installed in the MBR of /dev/nvme1n1.

You have UEFI system, so never should have a boot loader in MBR. Difficult to erase, but as long as you do not attempt to boot in old BIOS mode, it is ok.

LDM is proprietary Microsoft volume manager. Used as a work around for the old MBR 4 partition limit. But gpt has a soft limit of 128 partitions, so LDM not required.
Microsoft also does not have an undo, and some Microsoft tools do not work on LDM.
Best to remove LDM, if possible.

Old links as dynamic partitions rarely seen any more with gpt partitioning.  Microsoft has required UEFI with gpt since 2012.

[http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS in fdisk, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx) & 
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)
[https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv) & 
[https://packages.ubuntu.com/search?keywords=ldmtool](https://packages.ubuntu.com/search?keywords=ldmtool)
[http://manpages.ubuntu.com/manpages/trusty/man1/ldmtool.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/ldmtool.1.html)
[https://askubuntu.com/questions/1227285/how-can-i-mount-a-microsoft-ldm-partition-in-ubuntu-18-04-lts-desktop](https://askubuntu.com/questions/1227285/how-can-i-mount-a-microsoft-ldm-partition-in-ubuntu-18-04-lts-desktop)

---

### Post by dragonfly41 on 2024-07-03
If you can get into Windows then try installing (leverage 14 days free trial) EasyUEFI and attack the boot problem there as one front.

---

