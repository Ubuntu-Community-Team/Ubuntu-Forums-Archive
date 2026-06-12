---
title: "Booting Problem"
date: 2024-05-20
forum: General Help
---

### Post by mytan1 on 2024-05-20
Hi all,

I have very little to no experience in Ubuntu and Grub rescue. However, I am in charge of a machine with a dual booting installation (i.e., Windows and Ubuntu). However, whenever the computer starts, it goes into Grub rescue. 

I searched online and found this website: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). The website told me in the "Using Boot-Repair" section to create a Boot-Info Summary button and share it on Ubuntu Forums along with a description of my boot issue, so that experienced forum members can advise. Once I get the green light from experienced forum members, I should click the Recommended repair button. When repair is finished, note the new URL (paste.ubuntu.com/XXXXX) that appeared on a paper, then reboot and check if I recovered access to my OSs - If the repair does not succeed, indicate the URL to people who can help me by email or forum. I obtained this Boot-Info Summary as follows:
```


boot-repair-4ppa2075                                              [20240520_0653]


============================== Boot Info Summary ===============================


 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt2)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdc.


sda1: __________________________________________________________________________


    File system:       
    Boot sector type:  Grub2's core.img
    Boot sector info: 


sda2: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/ubuntu/fwupx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg


sda3: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sda4: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.6 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub


sdb1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb2: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi 
                       /efi/Microsoft/Boot/SecureBootRecovery.efi 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi


sdb3: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


sdb4: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8 or 10
    Boot files:        /Windows/System32/winload.exe


sdb5: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdc1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 6.04
    Boot sector info:  Syslinux looks at sector 32864 of /dev/sdc1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/boot/bootx64.efi /efi/boot/grubx64.efi 
                       /efi/boot/mmx64.efi /ldlinux.sys




================================ 2 OS detected =================================


OS#1:   Ubuntu 16.04.6 LTS on sda4
OS#2:   Windows 8 or 10 on sdb4


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: GA102 [GeForce RTX 3080 Ti] GA102 [GeForce RTX 3090] from NVIDIA Corporation NVIDIA Corporation
Live-session OS is Linuxmint 64-bit (Linux Mint 21.2, victoria, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: 4001(5.11) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot enabled.
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0002,0001,0003,0000,0004
Boot0000* Windows Boot Manager    HD(2,GPT,a6c249dc-0ca4-4217-af0b-e74b6030e5c2,0xfa000,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...7................
Boot0001* Hard Drive    BBS(HD,,0x0)..GO..NO........o.W.D.C. .W.D.6.0.E.F.R.X.-.6.8.L.0.B.N.1....................A...........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.X.W.1.1.5.D.P.7.L.C.Y.4........BO..NO..........K.i.n.g.s.t.o.n. .S.H.P.M.2.2.8.0.P.2./.9.6.0.G....................A........................1.N........>.;......F..Gd-.;.A..MQ..L.K.i.n.g.s.t.o.n. .S.H.P.M.2.2.8.0.P.2./.9.6.0.G........BO..NO.........K.i.n.g.s.t.o.n.D.a.t.a.T.r.a.v.e.l.e.r. .3...0.P.M.A.P....................A...................................F..Gd-.;.A..MQ..L.4.C.E.D.F.B.7.4.A.3.2.F.E.2.C.0.8.2.B.5.0.7.3.7........BO
Boot0002* ubuntu    HD(2,GPT,49127866-a1be-410d-bb16-de50eaa90e01,0x1000,0x100800)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0003* ubuntu    HD(2,GPT,49127866-a1be-410d-bb16-de50eaa90e01,0x1000,0x100800)/File(\EFI\UBUNTU\GRUBX64.EFI)..BO
Boot0004* UEFI: KingstonDataTraveler 3.0PMAP, Partition 1    PciRoot(0x0)/Pci(0x1d,0x0)/USB(0,0)/USB(5,0)/USB(2,0)/HD(1,MBR,0x3e7f325f,0x800,0x39cb800)..BO


82894bcbe4f010664226ba7591372538   sda2/ubuntu/fwupx64.efi
6e3d0052641cc935572b09028ed698e8   sda2/ubuntu/grubx64.efi
4487628005555bfd4a4c0a47211e0700   sda2/ubuntu/mmx64.efi
f7a57b08bc7c1c85417ae4cea582d1d4   sda2/ubuntu/shimx64.efi
3d09cb6ae9b7dfb474846879b12bd1f9   sdb2/Boot/bootx64.efi
23837e7f81b5b729c2cc673d3da56273   sdb2/Microsoft/Boot/SecureBootRecovery.efi
3d09cb6ae9b7dfb474846879b12bd1f9   sdb2/Microsoft/Boot/bootmgfw.efi
b3d8489beeed8806075fc70173f0908a   sdb2/Microsoft/Boot/bootmgr.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
sdb    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda4    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB
sdb1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdb2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdb4    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdb5    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far


Partitions info (2/3): _________________________________________________________


sda2    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda4    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
sdb2    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb4    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot


Partitions info (3/3): _________________________________________________________


sda2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda4    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sdb1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdb2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdb4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdb5    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sda1    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 5.46 TiB, 6001175126016 bytes, 11721045168 sectors
Disk identifier: B57E6071-8779-45EB-99A4-A2DD3D3D08D4
           Start         End     Sectors  Size Type
sda1         2048        4095        2048    1M Linux filesystem
sda2         4096     1054719     1050624  513M EFI System
sda3  11587012608 11721043967   134031360 63.9G Linux swap
sda4      1054720 11587012607 11585957888  5.4T Linux filesystem
Partition table entries are not in disk order.
Disk sdb: 894.25 GiB, 960197124096 bytes, 1875385008 sectors
Disk identifier: 8250032F-6DCC-4478-91AA-457CD8128039
         Start        End    Sectors   Size Type
sdb1       2048    1023999    1021952   499M Windows recovery environment
sdb2    1024000    1228799     204800   100M EFI System
sdb3    1228800    1261567      32768    16M Microsoft reserved
sdb4    1261568  135723007  134461440  64.1G Microsoft basic data
sdb5  135723008 1875382271 1739659264 829.5G Microsoft basic data
Disk sdc: 28.9 GiB, 31029460992 bytes, 60604416 sectors
Disk identifier: 0x3e7f325f
     Boot Start      End  Sectors  Size Id Type
sdc1  *     2048 60604415 60602368 28.9G  c W95 FAT32 (LBA)


parted -lm (filtered): _________________________________________________________


sda:6001GB:scsi:512:4096:gpt:ATA WDC WD60EFRX-68L:;
1:1049kB:2097kB:1049kB:::;
2:2097kB:540MB:538MB:fat32:EFI System Partition:boot, esp;
4:540MB:5933GB:5932GB:ext4::;
3:5933GB:6001GB:68.6GB:linux-swap(v1)::swap;
sdb:960GB:scsi:512:4096:gpt:ATA Kingston SHPM228:;
1:1049kB:524MB:523MB:ntfs:Basic data partition:hidden, diag;
2:524MB:629MB:105MB:fat32:EFI system partition:boot, esp;
3:629MB:646MB:16.8MB::Microsoft reserved partition:msftres;
4:646MB:69.5GB:68.8GB:ntfs:Basic data partition:msftdata;
5:69.5GB:960GB:891GB:ntfs:Basic data partition:msftdata;
sdc:31.0GB:scsi:512:512:msdos:Kingston DataTraveler 3.0:;
1:1049kB:31.0GB:31.0GB:fat32::boot, lba;


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                   
&#9500;&#9472;sda1                                               88c6bdb6-ca92-47a2-b793-5a074b26b82e             
&#9500;&#9472;sda2 vfat     4E5A-DA98                            49127866-a1be-410d-bb16-de50eaa90e01             EFI System Partition
&#9500;&#9472;sda3 swap     18a9e92f-15bb-4f29-874f-ca10f588b77e 055563b7-5887-48bc-a742-c4d0f3243295             
&#9492;&#9472;sda4 ext4     f05fd1e2-88d9-4567-b872-180a78b0da03 39ad1089-0702-4b0d-80fe-2a8dfd343d77             
sdb                                                                                                   
&#9500;&#9472;sdb1 ntfs     14D46C6AD46C4FD2                     e6295d06-a6ec-4292-8858-87101ea75cd5 Recovery    Basic data partition
&#9500;&#9472;sdb2 vfat     5A6E-2F26                            a6c249dc-0ca4-4217-af0b-e74b6030e5c2             EFI system partition
&#9500;&#9472;sdb3                                               a997dc59-ca1f-4b91-bdea-933821fd035a             Microsoft reserved partition
&#9500;&#9472;sdb4 ntfs     5CF89CA5F89C7EC8                     9aca27b9-0d08-41ca-85ff-1bf40844c16b             Basic data partition
&#9492;&#9472;sdb5 ntfs     B436365836361BB4                     8b372540-7fd6-46d1-82d6-cabcb29708e2 SSD         Basic data partition
sdc                                                                                                   
&#9492;&#9472;sdc1 vfat     00AB-1D19                            3e7f325f-01                          BOOT-REPAIR 


Mount points (filtered): _______________________________________________________


            Avail Use% Mounted on
/dev/sda2   508.3M   1% /mnt/boot-sav/sda2
/dev/sda4     4.5T  10% /mnt/boot-sav/sda4
/dev/sdb1    68.2M  86% /mnt/boot-sav/sdb1
/dev/sdb2    69.2M  28% /mnt/boot-sav/sdb2
/dev/sdb4     6.5G  90% /mnt/boot-sav/sdb4
/dev/sdb5   107.4G  87% /mnt/boot-sav/sdb5
/dev/sdc1    26.4G   9% /cdrom


Mount options (filtered): ______________________________________________________


/dev/sda2   vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda4   ext4            rw,relatime
/dev/sdb1   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdb2   vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sdb4   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdb5   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdc1   vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro


===================== sda2/efi/ubuntu/grub.cfg (filtered) ======================


search.fs_uuid f05fd1e2-88d9-4567-b872-180a78b0da03 root hd0,gpt4 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


====================== sda4/boot/grub/grub.cfg (filtered) ======================


Ubuntu   f05fd1e2-88d9-4567-b872-180a78b0da03
### END /etc/grub.d/30_os-prober ###
System setup   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###


========================== sda4/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=f05fd1e2-88d9-4567-b872-180a78b0da03 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=4E5A-DA98  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=18a9e92f-15bb-4f29-874f-ca10f588b77e none            swap    sw              0       0


======================= sda4/etc/default/grub (filtered) =======================


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


==================== sda4: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
3882.688488007 = 4169.005019136 boot/grub/grub.cfg                             1
   5.165893555 = 5.546835968    boot/vmlinuz-4.4.0-174-generic                 1
   2.150268555 = 2.308833280    boot/vmlinuz-4.4.0-176-generic                 1
   6.892284393 = 7.400534016    boot/vmlinuz-4.4.0-177-generic                 1
   6.892284393 = 7.400534016    vmlinuz                                        1
   2.150268555 = 2.308833280    vmlinuz.old                                    1
   5.452976227 = 5.855088640    boot/initrd.img-4.4.0-174-generic              4
   2.490333557 = 2.673975296    boot/initrd.img-4.4.0-176-generic              5
   7.411842346 = 7.958405120    boot/initrd.img-4.4.0-177-generic              3
   7.411842346 = 7.958405120    initrd.img                                     3
   2.490333557 = 2.673975296    initrd.img.old                                 5


===================== sda4: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 12512 Mar 21  2018 10_linux
-rwxr-xr-x 1 root root 11082 Jun 17  2016 20_linux_xen
-rwxr-xr-x 1 root root 11692 Jun 17  2016 30_os-prober
-rwxr-xr-x 1 root root  1418 Jun 17  2016 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jun 17  2016 40_custom
-rwxr-xr-x 1 root root   216 Jun 17  2016 41_custom


====================== sdc1/boot/grub/grub.cfg (filtered) ======================


Start Boot-Repair-Disk 64-bit
Start Boot-Repair-Disk 64-bit (compatibility mode)
UEFI Firmware Settings
Test memory


========================= sdc1/syslinux.cfg (filtered) =========================


DEFAULT loadconfig


LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/


==================== sdc1: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1


================== sdc1: Location of files loaded by Syslinux ==================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1






Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of
sda4,
using the following options:  sda2/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file


Final advice in case of suggested repair: ______________________________________


Please do not forget to make your UEFI firmware boot on the Ubuntu 16.04.6 LTS entry (sda2/efi/****/shim****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\shim****.efi (**** will be updated in the final message)


*******.us ko ()
```



The summary can also be found on this website: [https://paste.ubuntu.com/p/JKFhRrWMjd/](https://paste.ubuntu.com/p/JKFhRrWMjd/). As I have little to no experience in grub rescue and Ubuntu, appreciate your advice and is it OK to click on the "Recommended Repair" button?

Thanks in advance and best regards,

Maxine Tan

---

### Post by ajgreeny on 2024-05-20
Hello Maxine and welcome to the forum.
I have added code tags to your post to make the boot-info report easier to read but in future just show us the pastebin link; no need to copy and paste the report as you did as the pastebin link contains it all.

See my signature below for a code-tags "how to".

---

### Post by tea for one on 2024-05-20
Ubuntu 16.04 is now unsupported.

Back up all the data from both Ubuntu and Windows 
Remove the disk sda, where Ubuntu is located
Boot Windows via PC boot menu

If Windows does not boot, you'll need Windows repair tools (available within a Windows install iso)
Please report back if Windows boots and then, we'll offer more advice about installing a supported version of Ubuntu

---

### Post by yancek on 2024-05-20
I don't know how you came to install Ubuntu 16.04 but you might read the link below to gain an understanding of release versions so you don't make the same mistake again.

 [https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)

You haven't indicated whether your windows on the other drive boots when selected in the BIOS so try that as suggested.  Also, you have done multiple installs as shown by the existence of a BIOS_boot partition as well as an EFI partition.  You should select either UEFI or Legacy.

If you have not done so already, I would suggest you read through the link below on how to install Ubuntu.

 [https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

---

### Post by oldfred on 2024-05-20
Since two drives, you do not have to have both systems in UEFI mode, but it is highly recommended.
Microsoft required vendors to install in UEFI boot mode to gpt partitioned drives since 2012 and release of Windows 8. So almost all systems are UEFI, but Microsoft allowed BIOS boot installs so older system could still use Windows 8.
New systems starting in 2020 are now UEFI only. My  newer Dell says "BIOS" but once in BIOS it says UEFI only.

You need to always choose UEFI boot mode of live installer or repair flash drives from UEFI/BIOS one time boot mode.
The boot mode setting in UEFI settings, if for installed systems. It has two (really 3) modes. UEFI or BIOS/CSM/Legacy. But within UEFI is UEFI Secure boot on or UEFI secure boot off.

---

### Post by mytan1 on 2024-05-22
Hi all,

Thank you for all your replies.

Thankfully, Windows boots up.

I have backed up all data.

I don't know how to remove the disk sda, where Ubuntu is located. I did not install Ubuntu nor Windows on this machine. I don't even know how to install Ubuntu. Sorry for my ignorance.

Appreciate your assistance and what are the next steps that I should take to install a supported version of Ubuntu?

Best regards,

Maxine

---

### Post by tea for one on 2024-05-22
> **mytan1 said:**
> Thankfully, Windows boots up
Good - one problem shelved
> **mytan1 said:**
> I have backed up all data.
Even better
> **mytan1 said:**
> I don't know how to remove the disk sda, where Ubuntu is located.
Learn how to physically remove/add disks (it will be easier to install Ubuntu when the Windows disk is inaccessible)
Explore your PC UEFI settings &#8211; you may be able to isolate a disk via settings
> **mytan1 said:**
> what are the next steps that I should take to install a supported version of Ubuntu?
Other than [https://ubuntu.com/desktop](https://ubuntu.com/desktop), familiarise yourself with Ubuntu flavours [https://ubuntu.com/desktop/flavours](https://ubuntu.com/desktop/flavours)
Decide which flavour(s) suit your needs - version 24.04 with LTS = Long Term Support
Make a bootable usb and Try before installing

---

### Post by yancek on 2024-05-22
The link below is to the site with a download of the most recent Ubuntu iso file (24.04) you can use to install Ubuntu.

[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

If you prefer a more stable release, you can download 22.04 at the site from the below link:

lhttps://releases.ubuntu.com/jammy/

The link below explains how to verify the iso file you downloaded is good and how to put it on a DVD/USB.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Details on the entire process including installing are at the Ubuntu site at the link below.  There are countless other sites explaining it so it is pointless for someone here to give all the details when they are readily available online.  .

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

I'd suggest reading through these sites entirely before beginning.  You need to be able to identify which drive to install to if you are not going to disconnect the windows drive so you do not accidentally overwrite windows.

I'm curious as to what  you mean by "I am in charge of a machine with a dual booting installation".  Is this a newly acquired computer or does it belong to someone else you are trying to help?

---

### Post by mytan1 on 2024-05-27
Hi all,

Thanks for your guidance/advice.

I purchased the workstation through a grant around 7 years ago. My student installed Ubuntu at the time.

Appreciate your advice and can I install the new version of Ubuntu without removing the disk sda, where the current Ubuntu is located? I'm concerned about messing up or overwriting Windows in some way.

Best regards,

Maxine

---

### Post by dragonfly41 on 2024-05-27
Because of your fears of screwing up the internal drive with Windows installed my advice, reading your experience,  would be to leave Windows well alone and concentrate on installing Ubuntu on an external SSD in a USB container and caddy.  
But advice depends on budget.
This approach regards your PC as the “mothership” and as I write now I am using Ubuntu 22.04 on an SSD in an external docking bay with SSD caddy. Performance is quite acceptable provided that you have a USB 3.0 (not 2.0) port to attach SSD and a powered docking bay or SSD container.
You will need to go through the process of creating a LiveUSB probably from Windows using Rufus to create a LiveUSB to install Ubuntu into the external SSD.
However such experiments depend on your budget to acquire an external USB container or better a separately powered dual ducking bay so that you can plug in two devices (main Ubuntu caddy in one bay and backup caddy in second bay).  
If you search this forum with keyword “StarTech” you will read where I give details of my dual boot setup.
Another bit of advice is to install rEFInd to switch between your Windows and (hopefully) external Ubuntu(s).
And finally when you boot into Windows, Google search externally for “EasyUEFI” and you can use their 15day free trial to test UEFI configuration.  But only start the trial when you have all the parts in play.


[P.S.] I should add the options of creating Ubuntu virtual machine on Windows, or having a Ubuntu desktop virtual machine in cloud such as Azure account (but again budget considerations).  We do not know how heavy your Ubuntu work load will be.

---

### Post by yancek on 2024-05-27
>  Appreciate your advice and can I install the new version of Ubuntu  without removing the disk sda, where the current Ubuntu is located? I

The suggestion above was to remove the windows disk (which showed as sdb) so as not to overwrite it when you install Ubuntu.
You can leave the windows disk in but when you boot the Ubuntu installer, you should use some Linux software to determine how these drives show up, something like fdisk or gparted which will be available on the install medium.  You need to verify at the time of the install what the drives are shown as.

---

### Post by dragonfly41 on 2024-05-27
> [COLOR=#000000]The suggestion above was to remove the windows disk ... 

Or simpler you can just pull out the powerlead inside the tower to disable the drive.[/COLOR]

---

