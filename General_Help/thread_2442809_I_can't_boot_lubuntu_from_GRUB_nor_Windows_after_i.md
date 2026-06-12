---
title: "I can't boot lubuntu from GRUB nor Windows after installation"
date: 2020-05-07
forum: General Help
---

### Post by campol on 2020-05-07
**I can't boot GRUB nor Windows boot manager after installation**

[B]So this is my first time installing a UNIX operating system so i chose lubuntu on my old computer and created a live usb, after "successfully" installing it and booting back in I could only log into Windows and looked up how to boot into lubunto changing the Boot Manager so I found this "guide" 

[https://itsfoss.com/no-grub-windows-linux/](https://itsfoss.com/no-grub-windows-linux/) 

where it tells you how to change the boot manager and entered the following commands:[/B]

[B]bcdedit /set {bootmgr} path \EFI\lubuntu\grubx64.efi

[/B]
**The command prompt marked the operation as successful so I restarted my PC and naturally it screwed up the boot manager and now it "can't find a boot manager or disk failed" so the same "guide" tells you to boot from a windows installation disk and after burning one and booting it from SATA0 it can't do that either it gives me the same error.**

**So the only way I can boot is running the lubuntu trial version from the USB. and i performed boot repair and this is the information I got, how do I proceed from here?**


boot-repair-4ppa102                                              [20200507_2037]


============================== Boot Info Summary ===============================


 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 
    1816348800 of the same hard drive for core.img. core.img is at this 
    location and looks for (,gpt5)/boot/grub. It also embeds following 
    components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------
 => Syslinux MBR (4.04-4.07) is installed in the MBR of /dev/sdf.


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda2: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/HP/SystemDiags/CryptRSA.efi 
                       /efi/HP/SystemDiags/CryptRSA32.efi 
                       /efi/HP/SystemDiags/SystemDiags.efi 
                       /efi/HP/SystemDiags/SystemDiags32.efi 
                       /efi/HP/SystemRecovery/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/Microsoft/Boot/memtest.efi


sda3: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


sda4: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe


sda5: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 19.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img


sda6: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda7: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd


sdf1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 19528 of /dev/sdf1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/menu.lst




================================ 3 OS detected =================================


OS#1:   Windows 8 on sda4
OS#2:   Ubuntu 19.10 on sda5
OS#3:   Windows Recovery Environment (boot) on sda7


============================ Architecture/Host Info ============================


CPU architecture: 64-bit
Live-session OS is Ubuntu 64-bit (Ubuntu 19.10, eoan, x86_64)


===================================== UEFI =====================================


BIOS is EFI-compatible, but it is not setup in EFI-mode for this live-session.


cb8e4284804d56f058c0e1cf111eeedd   sda2/Boot/bootx64.efi
6488d391f74263c9da3c3d47dffa6212   sda2/HP/SystemDiags/CryptRSA.efi
1b8c0684ede8539ccc205cf7a750eca3   sda2/HP/SystemDiags/CryptRSA32.efi
0c2035ed413a8f352b7d315121f2d8c0   sda2/HP/SystemDiags/SystemDiags.efi
d39ce8435f3b31816bd72676fd528de8   sda2/HP/SystemDiags/SystemDiags32.efi
87b6d22295a16073d8d456fc574441a8   sda2/HP/SystemRecovery/bootmgfw.efi
cb8e4284804d56f058c0e1cf111eeedd   sda2/Microsoft/Boot/bootmgfw.efi
3df357ffd0654bb80f2a575485e6e0cc   sda2/Microsoft/Boot/bootmgr.efi
ff6d345785671fbcea9561a3cbc47702   sda7/Boot/bootx64.efi
2d6c4295c7b479c60687d82ae80421b7   sda7/Boot/bootx64.efi.efi
9f1c9510b4c944decbb563a3dbe39e6d   sda7/Microsoft/Boot/cdboot.efi
acc978f561b2b06c5cf241ce37439fa2   sda7/Microsoft/Boot/cdboot_noprompt.efi




============================= Drive/Partition Info =============================




Disks info: ____________________________________________________________________


sda	: GPT,	noBIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	2048 sectors * 512 bytes
sdf	: not-GPT,	noBIOSboot,	has-noESP, 	usb-disk,	not-mmc, no-os,	2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda1	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sda2	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sda4	: is-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
sda6	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
sda7	: is-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
sdf1	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sda5	: is-os,	64, apt-get,	grub-pc ,	grub2,	grub-install,	grubenv-ok,	update-grub,	farbios


Partitions info (2/3): _________________________________________________________


sda1	: isnotESP,	part-has-no-fstab,	notbiosboot,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot
sda2	: is---ESP,	part-has-no-fstab,	notbiosboot,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda4	: isnotESP,	part-has-no-fstab,	notbiosboot,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	is-winboot
sda6	: isnotESP,	part-has-no-fstab,	notbiosboot,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot
sda7	: isnotESP,	part-has-no-fstab,	notbiosboot,	no-nt,	no-winload,	recovery-or-hidden,	bootmgr,	is-winboot
sdf1	: isnotESP,	part-has-no-fstab,	notbiosboot,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda5	: isnotESP,	fstab-without-efi,	notbiosboot,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot


Partitions info (3/3): _________________________________________________________


sda1	: not-sepboot,	no-boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	std-grub.d,	sda
sda2	: not-sepboot,	no-boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	std-grub.d,	sda
sda4	: not-sepboot,	no-boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	std-grub.d,	sda
sda6	: not-sepboot,	no-boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	std-grub.d,	sda
sda7	: not-sepboot,	no-boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	std-grub.d,	sda
sdf1	: is-sepboot,	no-kernel,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	std-grub.d,	sdf
sda5	: not-sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sda


fdisk -l (filtered): ___________________________________________________________


        Boot   Start     End Sectors  Size Id Type
loop0p1 *          0 3283711 3283712  1.6G  0 Empty
loop0p2      3257860 3265795    7936  3.9M ef EFI (FAT-12/16/32)
Disk sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
           Start        End    Sectors   Size Type
sda1        2048    2097151    2095104  1023M Windows recovery environment
sda2     2097152    2834431     737280   360M EFI System
sda3     2834432    3096575     262144   128M Microsoft reserved
sda4     3096576 1707017618 1703921043 812.5G Microsoft basic data
sda5  1707018240 1911816191  204797952  97.7G Linux filesystem
sda6  1911818240 1912870911    1052672   514M Windows recovery environment
sda7  1912870912 1953523711   40652800  19.4G Microsoft basic data
Disk sdf: 7.27 GiB, 7803174912 bytes, 15240576 sectors
      Boot Start      End  Sectors  Size Id Type
sdf1  *     8064 15240575 15232512  7.3G  7 HPFS/NTFS/exFAT
Disk zram0: 1.15 GiB, 1226534912 bytes, 299447 sectors
Disk zram1: 1.15 GiB, 1226534912 bytes, 299447 sectors
Disk zram2: 1.15 GiB, 1226534912 bytes, 299447 sectors
Disk zram3: 1.15 GiB, 1226534912 bytes, 299447 sectors


parted -lm (filtered): _________________________________________________________


sda:1000GB:scsi:512:4096:gpt:ATA WDC WD10EZEX-60Z:;
1:1049kB:1074MB:1073MB:ntfs:Basic data partition:hidden, diag;
2:1074MB:1451MB:377MB:fat32:EFI system partition:boot, esp;
3:1451MB:1585MB:134MB::Microsoft reserved partition:msftres;
4:1585MB:874GB:872GB:ntfs:Basic data partition:msftdata;
5:874GB:979GB:105GB:ext4::;
6:979GB:979GB:539MB:ntfs::hidden, diag;
7:979GB:1000GB:20.8GB:ntfs:Basic data partition:hidden, msftdata;
sdf:7803MB:scsi:512:512:msdos:Kingston DataTraveler 2.0:;
1:4129kB:7803MB:7799MB:ntfs::boot;
zram3:1227MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1227MB:1227MB:linux-swap(v1)::;
zram1:1227MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1227MB:1227MB:linux-swap(v1)::;
zram2:1227MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1227MB:1227MB:linux-swap(v1)::;
zram0:1227MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1227MB:1227MB:linux-swap(v1)::;


blkid (filtered): ______________________________________________________________


NAME  FSTYPE   UUID                                 PARTUUID                             LABEL               PARTLABEL
sda                                                                                                          
sda1  ntfs     72E869BFE8698269                     65d6f5af-d903-4200-84a1-23e8ce1c139e Windows RE tools    Basic data partition
sda2  vfat     64B5-5C36                            c2949a00-a361-44d0-b4f6-4f2ce551d273 SYSTEM              EFI system partition
sda3                                                2a494061-1e73-465c-91ae-80e4cca6924b                     Microsoft reserved partition
sda4  ntfs     244079FD4079D5D0                     8ec6ab96-c56b-4117-aaa9-98c04fd7f7dc OS                  Basic data partition
sda5  ext4     912fa4dc-4b58-4999-a2b4-2a6b1ce6dac4 ca47f1ae-0c6c-4cf9-ab94-b1fc7d358712                     
sda6  ntfs     24DCF0ADDCF07A7E                     18268f92-9ed3-4b42-82f9-89b0ebf37e99                     
sda7  ntfs     7804FEC704FE8780                     3873d5cb-8737-4bea-bdb8-54a69eebc1fa Recovery Image      Basic data partition
sdf                                                                                                          
sdf1  ntfs     902C464B2C462C92                     c3072e18-01                          UUI                 
zram0                                                                                                        
zram1                                                                                                        
zram2                                                                                                        
zram3                                                                                                        


df (filtered): _________________________________________________________________


       Avail Use% Mounted on
sda1   676.4M  34% /mnt/boot-sav/sda1
sda2   321.9M  10% /mnt/boot-sav/sda2
sda4   273.4G  66% /mnt/boot-sav/sda4
sda5    86.3G   5% /mnt/boot-sav/sda5
sda6    86.4M  83% /mnt/boot-sav/sda6
sda7   516.7M  97% /mnt/boot-sav/sda7
sdf1     5.6G  23% /isodevice


Mount options: __________________________________________________________________


sda1   rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
sda2   rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
sda4   ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096
sda5   rw,relatime
sda6   rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
sda7   rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
sdf1   rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096


====================== sda5/boot/grub/grub.cfg (filtered) ======================


Ubuntu
Ubuntu, with Linux 5.3.0-18-generic
Windows 8 (on /dev/sda4)
Windows Recovery Environment (on /dev/sda7)
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###


========================== sda5/etc/fstab (filtered) ===========================


# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=912fa4dc-4b58-4999-a2b4-2a6b1ce6dac4 /              ext4    defaults   0 1


======================= sda5/etc/default/grub (filtered) =======================


GRUB_DEFAULT=1
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR='Ubuntu'
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
#GRUB_TERMINAL=console
#GRUB_GFXMODE=640x480
#GRUB_DISABLE_LINUX_UUID=true
#GRUB_DISABLE_RECOVERY="true"
#GRUB_INIT_TUNE="480 440 1"


==================== sda5: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)


 899.343143463 = 965.662347264  boot/grub/grub.cfg                             3
 866.102622986 = 929.970610176  boot/grub/i386-pc/core.img                     1
 904.180660248 = 970.856591360  boot/vmlinuz                                   2
 904.180660248 = 970.856591360  boot/vmlinuz-5.3.0-18-generic                  2
 904.180660248 = 970.856591360  boot/vmlinuz.old                               2
 904.293853760 = 970.978131968  boot/initrd.img                                2
 904.293853760 = 970.978131968  boot/initrd.img-5.3.0-18-generic               2
 904.293853760 = 970.978131968  boot/initrd.img.old                            2


====================== sdf1/boot/grub/menu.lst (filtered) ======================


# This Menu created with Universal USB Installer [https://www.pendrivelinux.com](https://www.pendrivelinux.com)
default 0
timeout 30
color NORMAL HIGHLIGHT HELPTEXT HEADING
foreground=FFFFFF
background=000000
title Boot lubuntu-19.10-desktop-amd64
set ISO=/lubuntu-19.10-desktop-amd64.iso
set CASPER=/casper-rw
find --set-root %ISO%
map %ISO% (0xff)
#CLUG
map --hook
root (0xff)
kernel /casper/vmlinuz file=/preseed/lubuntu.seed noprompt boot=casper iso-scan/filename=%ISO% quiet --
initrd /casper/initrd
title Boot lubuntu-19.10-desktop-amd64 acpi=off
set ISO=/lubuntu-19.10-desktop-amd64.iso
set CASPER=/casper-rw
find --set-root %ISO%
map %ISO% (0xff)
#CLUG
map --hook
root (0xff)
kernel /casper/vmlinuz file=/preseed/lubuntu.seed noprompt boot=casper iso-scan/filename=%ISO% quiet acpi=off --
initrd /casper/initrd


==================== sdf1: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)


            ?? = ??             boot/grub/menu.lst                             1
            ?? = ??             vmlinuz                                        1
            ?? = ??             initrd                                         1




========= Devices which don't seem to have a corresponding hard drive ==========


sdb sdc sdd sde 




=============================== StdErr Messages ================================


  /dev/sdb: open failed: No medium found
  /dev/sdc: open failed: No medium found
  /dev/sdd: open failed: No medium found
  /dev/sde: open failed: No medium found


Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would purge (in order to fix packages) and reinstall the grub-efi-amd64-signed of
sda5,
using the following options:        sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s  use-standard-efi-file    


Blockers in case of suggested repair: __________________________________________


The current session is in Legacy mode. Please reboot the computer, and use this software in an EFI session. This will enable this feature. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd](www.sourceforge.net/p/boot-repair-cd)), after making sure your BIOS is set up to boot USB in EFI mode. 


Advice in case of suggested repair: ____________________________________________


The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
Do you want to continue?


Final advice in case of suggested repair: ______________________________________


Please do not forget to make your BIOS boot on sda2/efi/****/shim****.efi (**** will be updated in the final message) file!


If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\shim****.efi (**** will be updated in the final message)


The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.


**Can someone please tell me how to boot from GRUB or change it back to windows?? Help would be greatly appreciated.**

---

### Post by yancek on 2020-05-07
See your other similar thread which has the answer.

---

### Post by oldfred on 2020-05-07
Thread closed.
Please do not post duplicate threads. 
We all are volunteers and need to know what already has been suggest to avoid duplicate effort.

See
[https://ubuntuforums.org/showthread.php?t=2442797](https://ubuntuforums.org/showthread.php?t=2442797)

---

