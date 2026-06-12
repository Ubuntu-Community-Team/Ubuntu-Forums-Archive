---
title: "I can't boot GRUB nor Windows boot manager after installation"
date: 2020-05-07
forum: General Help
---

### Post by campol on 2020-05-07
So this is my first time installing a UNIX operating system so i chose lubuntu on my old computer and created a live usb, after "successfully" installing it and booting back in I could only log into Windows and looked up how to boot into lubunto changing the Boot Manager so I found this "guide" [https://itsfoss.com/no-grub-windows-linux/](https://itsfoss.com/no-grub-windows-linux/) where it tells you how to change the boot manager and entered the following commands:

bcdedit /set {bootmgr} path \EFI\lubuntu\grubx64.efi
The command prompt marked the operation as successful so I restarted my PC and naturally it screwed up the boot manager and now it "can't find a boot manager or disk failed" so the same "guide" tells you to boot from a windows installation disk and after burning one and booting it from SATA0 it can't do that either it gives me the same error.

So the only way I can boot is running the lubuntu trial version from the USB. 

Can someone please tell me how to boot from GRUB or change it back to windows?? Help would be greatly appreciated.

---

### Post by yancek on 2020-05-07
You don't indicate which windows you are using?  Is your windows  an EFI install? Did you install Lubuntu UEFI?
I would suggest going to the site at the link below and downloading boot repair using the 2nd option on that page while you are booted into the Lubuntu install usb.  Make sure that when you run boot repair that you select ONLY the Create BootInfo Summary option and do NOT try to make any repairs.  When boot repair finishes, it should give you a link which you can post here.  That should give member enough useful information so they can point you in the right direction.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by campol on 2020-05-07
Thank you this is what I got

```
boot-repair-4ppa102                                              [COLOR=#666666][[/COLOR]20200507_2037[COLOR=#666666]][/COLOR]

[COLOR=#666666]==============================[/COLOR] Boot Info [COLOR=#B8860B]Summary[/COLOR] [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v2.00[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 
    [COLOR=#666666]1816348800[/COLOR] of the same hard drive [COLOR=#AA22FF]**for**[/COLOR] core.img. core.img is at this 
    location and looks [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR],gpt5[COLOR=#666666])[/COLOR]/boot/grub. It also embeds following 
    components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------
 [COLOR=#666666]=[/COLOR]> Syslinux MBR [COLOR=#666666]([/COLOR][COLOR=#666666]4[/COLOR].04-4.07[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows [COLOR=#666666]8[/COLOR]/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows [COLOR=#666666]8[/COLOR]/2012: FAT32
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
    Boot sector type:  Windows [COLOR=#666666]7[/COLOR]/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows [COLOR=#666666]8[/COLOR]
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu [COLOR=#666666]19[/COLOR].10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows [COLOR=#666666]8[/COLOR]/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows [COLOR=#666666]8[/COLOR]/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdf1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  SYSLINUX [COLOR=#666666]4[/COLOR].07 [COLOR=#666666]2013[/COLOR]-07-25
    Boot sector info:  Syslinux looks at sector [COLOR=#666666]19528[/COLOR] of /dev/sdf1 [COLOR=#AA22FF]**for**[/COLOR] its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/menu.lst


[COLOR=#666666]================================[/COLOR] [COLOR=#666666]3[/COLOR] OS [COLOR=#B8860B]detected[/COLOR] [COLOR=#666666]=================================[/COLOR]

OS#1:   Windows [COLOR=#666666]8[/COLOR] on sda4
OS#2:   Ubuntu [COLOR=#666666]19[/COLOR].10 on sda5
OS#3:   Windows Recovery Environment [COLOR=#666666]([/COLOR]boot[COLOR=#666666])[/COLOR] on [COLOR=#B8860B]sda7[/COLOR]

[COLOR=#666666]============================[/COLOR] Architecture/Host [COLOR=#B8860B]Info[/COLOR] [COLOR=#666666]============================[/COLOR]

CPU architecture: [COLOR=#666666]64[/COLOR]-bit
Live-session OS is Ubuntu [COLOR=#666666]64[/COLOR]-bit [COLOR=#666666]([/COLOR]Ubuntu [COLOR=#666666]19[/COLOR].10, eoan, x86_64[COLOR=#666666])[/COLOR]

[COLOR=#666666]=====================================[/COLOR] [COLOR=#B8860B]UEFI[/COLOR] [COLOR=#666666]=====================================[/COLOR]

BIOS is EFI-compatible, but it is not setup in EFI-mode [COLOR=#AA22FF]**for**[/COLOR] this live-session.

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


[COLOR=#666666]=============================[/COLOR] Drive/Partition [COLOR=#B8860B]Info[/COLOR] [COLOR=#666666]=============================[/COLOR]


Disks info: ____________________________________________________________________

sda    : GPT,    noBIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    [COLOR=#666666]2048[/COLOR] sectors * [COLOR=#666666]512[/COLOR] bytes
sdf    : not-GPT,    noBIOSboot,    has-noESP,     usb-disk,    not-mmc, no-os,    [COLOR=#666666]2048[/COLOR] sectors * [COLOR=#666666]512[/COLOR] bytes

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________

sda1    : no-os,    [COLOR=#666666]32[/COLOR], nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : no-os,    [COLOR=#666666]32[/COLOR], nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda4    : is-os,    [COLOR=#666666]32[/COLOR], nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda6    : no-os,    [COLOR=#666666]32[/COLOR], nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda7    : is-os,    [COLOR=#666666]32[/COLOR], nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdf1    : no-os,    [COLOR=#666666]32[/COLOR], nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda5    : is-os,    [COLOR=#666666]64[/COLOR], apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]2[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________

sda1    : isnotESP,    part-has-no-fstab,    notbiosboot,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
sda2    : is---ESP,    part-has-no-fstab,    notbiosboot,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda4    : isnotESP,    part-has-no-fstab,    notbiosboot,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot
sda6    : isnotESP,    part-has-no-fstab,    notbiosboot,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
sda7    : isnotESP,    part-has-no-fstab,    notbiosboot,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,    is-winboot
sdf1    : isnotESP,    part-has-no-fstab,    notbiosboot,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda5    : isnotESP,    fstab-without-efi,    notbiosboot,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]3[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________

sda1    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda2    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda4    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda6    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda7    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sdf1    : is-sepboot,    no-kernel,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sdf
sda5    : not-sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ___________________________________________________________

        Boot   Start     End Sectors  Size Id Type
loop0p1 *          [COLOR=#666666]0[/COLOR] [COLOR=#666666]3283711[/COLOR] [COLOR=#666666]3283712[/COLOR]  [COLOR=#666666]1[/COLOR].6G  [COLOR=#666666]0[/COLOR] Empty
loop0p2      [COLOR=#666666]3257860[/COLOR] [COLOR=#666666]3265795[/COLOR]    [COLOR=#666666]7936[/COLOR]  [COLOR=#666666]3[/COLOR].9M ef EFI [COLOR=#666666]([/COLOR]FAT-12/16/32[COLOR=#666666])[/COLOR]
Disk sda: [COLOR=#666666]931[/COLOR].53 GiB, [COLOR=#666666]1000204886016[/COLOR] bytes, [COLOR=#666666]1953525168[/COLOR] sectors
           Start        End    Sectors   Size Type
sda1        [COLOR=#666666]2048[/COLOR]    [COLOR=#666666]2097151[/COLOR]    [COLOR=#666666]2095104[/COLOR]  1023M Windows recovery environment
sda2     [COLOR=#666666]2097152[/COLOR]    [COLOR=#666666]2834431[/COLOR]     [COLOR=#666666]737280[/COLOR]   360M EFI System
sda3     [COLOR=#666666]2834432[/COLOR]    [COLOR=#666666]3096575[/COLOR]     [COLOR=#666666]262144[/COLOR]   128M Microsoft reserved
sda4     [COLOR=#666666]3096576[/COLOR] [COLOR=#666666]1707017618[/COLOR] [COLOR=#666666]1703921043[/COLOR] [COLOR=#666666]812[/COLOR].5G Microsoft basic data
sda5  [COLOR=#666666]1707018240[/COLOR] [COLOR=#666666]1911816191[/COLOR]  [COLOR=#666666]204797952[/COLOR]  [COLOR=#666666]97[/COLOR].7G Linux filesystem
sda6  [COLOR=#666666]1911818240[/COLOR] [COLOR=#666666]1912870911[/COLOR]    [COLOR=#666666]1052672[/COLOR]   514M Windows recovery environment
sda7  [COLOR=#666666]1912870912[/COLOR] [COLOR=#666666]1953523711[/COLOR]   [COLOR=#666666]40652800[/COLOR]  [COLOR=#666666]19[/COLOR].4G Microsoft basic data
Disk sdf: [COLOR=#666666]7[/COLOR].27 GiB, [COLOR=#666666]7803174912[/COLOR] bytes, [COLOR=#666666]15240576[/COLOR] sectors
      Boot Start      End  Sectors  Size Id Type
sdf1  *     [COLOR=#666666]8064[/COLOR] [COLOR=#666666]15240575[/COLOR] [COLOR=#666666]15232512[/COLOR]  [COLOR=#666666]7[/COLOR].3G  [COLOR=#666666]7[/COLOR] HPFS/NTFS/exFAT
Disk zram0: [COLOR=#666666]1[/COLOR].15 GiB, [COLOR=#666666]1226534912[/COLOR] bytes, [COLOR=#666666]299447[/COLOR] sectors
Disk zram1: [COLOR=#666666]1[/COLOR].15 GiB, [COLOR=#666666]1226534912[/COLOR] bytes, [COLOR=#666666]299447[/COLOR] sectors
Disk zram2: [COLOR=#666666]1[/COLOR].15 GiB, [COLOR=#666666]1226534912[/COLOR] bytes, [COLOR=#666666]299447[/COLOR] sectors
Disk zram3: [COLOR=#666666]1[/COLOR].15 GiB, [COLOR=#666666]1226534912[/COLOR] bytes, [COLOR=#666666]299447[/COLOR] sectors

parted -lm [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: _________________________________________________________

sda:1000GB:scsi:512:4096:gpt:ATA WDC WD10EZEX-60Z:;
[COLOR=#666666]1[/COLOR]:1049kB:1074MB:1073MB:ntfs:Basic data partition:hidden, diag;
[COLOR=#666666]2[/COLOR]:1074MB:1451MB:377MB:fat32:EFI system partition:boot, esp;
[COLOR=#666666]3[/COLOR]:1451MB:1585MB:134MB::Microsoft reserved partition:msftres;
[COLOR=#666666]4[/COLOR]:1585MB:874GB:872GB:ntfs:Basic data partition:msftdata;
[COLOR=#666666]5[/COLOR]:874GB:979GB:105GB:ext4::;
[COLOR=#666666]6[/COLOR]:979GB:979GB:539MB:ntfs::hidden, diag;
[COLOR=#666666]7[/COLOR]:979GB:1000GB:20.8GB:ntfs:Basic data partition:hidden, msftdata;
sdf:7803MB:scsi:512:512:msdos:Kingston DataTraveler [COLOR=#666666]2[/COLOR].0:;
[COLOR=#666666]1[/COLOR]:4129kB:7803MB:7799MB:ntfs::boot;
zram3:1227MB:unknown:4096:4096:loop:Unknown:;
[COLOR=#666666]1[/COLOR]:0.00B:1227MB:1227MB:linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]::;
zram1:1227MB:unknown:4096:4096:loop:Unknown:;
[COLOR=#666666]1[/COLOR]:0.00B:1227MB:1227MB:linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]::;
zram2:1227MB:unknown:4096:4096:loop:Unknown:;
[COLOR=#666666]1[/COLOR]:0.00B:1227MB:1227MB:linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]::;
zram0:1227MB:unknown:4096:4096:loop:Unknown:;
[COLOR=#666666]1[/COLOR]:0.00B:1227MB:1227MB:linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]::;

blkid [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ______________________________________________________________

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

df [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: _________________________________________________________________

       Avail Use% Mounted on
sda1   [COLOR=#666666]676[/COLOR].4M  [COLOR=#666666]34[/COLOR]% /mnt/boot-sav/sda1
sda2   [COLOR=#666666]321[/COLOR].9M  [COLOR=#666666]10[/COLOR]% /mnt/boot-sav/sda2
sda4   [COLOR=#666666]273[/COLOR].4G  [COLOR=#666666]66[/COLOR]% /mnt/boot-sav/sda4
sda5    [COLOR=#666666]86[/COLOR].3G   [COLOR=#666666]5[/COLOR]% /mnt/boot-sav/sda5
sda6    [COLOR=#666666]86[/COLOR].4M  [COLOR=#666666]83[/COLOR]% /mnt/boot-sav/sda6
sda7   [COLOR=#666666]516[/COLOR].7M  [COLOR=#666666]97[/COLOR]% /mnt/boot-sav/sda7
sdf1     [COLOR=#666666]5[/COLOR].6G  [COLOR=#666666]23[/COLOR]% /isodevice

Mount options: __________________________________________________________________

sda1   rw,relatime,user_id[COLOR=#666666]=[/COLOR][COLOR=#666666]0[/COLOR],group_id[COLOR=#666666]=[/COLOR][COLOR=#666666]0[/COLOR],allow_other,blksize[COLOR=#666666]=[/COLOR][COLOR=#666666]4096[/COLOR]
sda2   rw,relatime,fmask[COLOR=#666666]=[/COLOR][COLOR=#666666]0022[/COLOR],dmask[COLOR=#666666]=[/COLOR][COLOR=#666666]0022[/COLOR],codepage[COLOR=#666666]=[/COLOR][COLOR=#666666]437[/COLOR],iocharset[COLOR=#666666]=[/COLOR]iso8859-1,shortname[COLOR=#666666]=[/COLOR]mixed,errors[COLOR=#666666]=[/COLOR]remount-ro
sda4   ro,relatime,user_id[COLOR=#666666]=[/COLOR][COLOR=#666666]0[/COLOR],group_id[COLOR=#666666]=[/COLOR][COLOR=#666666]0[/COLOR],allow_other,blksize[COLOR=#666666]=[/COLOR][COLOR=#666666]4096[/COLOR]
sda5   rw,relatime
sda6   rw,relatime,user_id[COLOR=#666666]=[/COLOR][COLOR=#666666]0[/COLOR],group_id[COLOR=#666666]=[/COLOR][COLOR=#666666]0[/COLOR],allow_other,blksize[COLOR=#666666]=[/COLOR][COLOR=#666666]4096[/COLOR]
sda7   rw,relatime,user_id[COLOR=#666666]=[/COLOR][COLOR=#666666]0[/COLOR],group_id[COLOR=#666666]=[/COLOR][COLOR=#666666]0[/COLOR],allow_other,blksize[COLOR=#666666]=[/COLOR][COLOR=#666666]4096[/COLOR]
sdf1   rw,relatime,user_id[COLOR=#666666]=[/COLOR][COLOR=#666666]0[/COLOR],group_id[COLOR=#666666]=[/COLOR][COLOR=#666666]0[/COLOR],allow_other,blksize[COLOR=#666666]=[/COLOR][COLOR=#B8860B]4096[/COLOR]

[COLOR=#666666]======================[/COLOR] sda5/boot/grub/grub.cfg [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]======================[/COLOR]

Ubuntu
Ubuntu, with Linux [COLOR=#666666]5[/COLOR].3.0-18-generic
Windows [COLOR=#666666]8[/COLOR] [COLOR=#666666]([/COLOR]on /dev/sda4[COLOR=#666666])[/COLOR]
Windows Recovery Environment [COLOR=#666666]([/COLOR]on /dev/sda7[COLOR=#666666])[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_os-prober ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_uefi-firmware ###*[/COLOR]

[COLOR=#666666]==========================[/COLOR] sda5/etc/fstab [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]===========================[/COLOR]

[COLOR=#008800]*# <file system>             <mount point>  <type>  <options>  <dump>  <pass>*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]912fa4dc-4b58-4999-a2b4-2a6b1ce6dac4 /              ext4    defaults   [COLOR=#666666]0[/COLOR] [COLOR=#B8860B]1[/COLOR]

[COLOR=#666666]=======================[/COLOR] sda5/etc/default/grub [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]=======================[/COLOR]

[COLOR=#B8860B]GRUB_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#666666]1[/COLOR]
[COLOR=#B8860B]GRUB_TIMEOUT_STYLE[/COLOR][COLOR=#666666]=[/COLOR]hidden
[COLOR=#B8860B]GRUB_TIMEOUT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#666666]0[/COLOR]
[COLOR=#B8860B]GRUB_DISTRIBUTOR[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'Ubuntu'[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"quiet splash"[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]""[/COLOR]
[COLOR=#008800]*#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"*[/COLOR]
[COLOR=#008800]*#GRUB_TERMINAL=console*[/COLOR]
[COLOR=#008800]*#GRUB_GFXMODE=640x480*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_LINUX_UUID=true*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_RECOVERY="true"*[/COLOR]
[COLOR=#008800]*#GRUB_INIT_TUNE="480 440 1"*[/COLOR]

[COLOR=#666666]====================[/COLOR] sda5: Location of files loaded by [COLOR=#B8860B]Grub[/COLOR] [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]

 [COLOR=#666666]899[/COLOR].343143463 [COLOR=#666666]=[/COLOR] [COLOR=#666666]965[/COLOR].662347264  boot/grub/grub.cfg                             [COLOR=#666666]3[/COLOR]
 [COLOR=#666666]866[/COLOR].102622986 [COLOR=#666666]=[/COLOR] [COLOR=#666666]929[/COLOR].970610176  boot/grub/i386-pc/core.img                     [COLOR=#666666]1[/COLOR]
 [COLOR=#666666]904[/COLOR].180660248 [COLOR=#666666]=[/COLOR] [COLOR=#666666]970[/COLOR].856591360  boot/vmlinuz                                   [COLOR=#666666]2[/COLOR]
 [COLOR=#666666]904[/COLOR].180660248 [COLOR=#666666]=[/COLOR] [COLOR=#666666]970[/COLOR].856591360  boot/vmlinuz-5.3.0-18-generic                  [COLOR=#666666]2[/COLOR]
 [COLOR=#666666]904[/COLOR].180660248 [COLOR=#666666]=[/COLOR] [COLOR=#666666]970[/COLOR].856591360  boot/vmlinuz.old                               [COLOR=#666666]2[/COLOR]
 [COLOR=#666666]904[/COLOR].293853760 [COLOR=#666666]=[/COLOR] [COLOR=#666666]970[/COLOR].978131968  boot/initrd.img                                [COLOR=#666666]2[/COLOR]
 [COLOR=#666666]904[/COLOR].293853760 [COLOR=#666666]=[/COLOR] [COLOR=#666666]970[/COLOR].978131968  boot/initrd.img-5.3.0-18-generic               [COLOR=#666666]2[/COLOR]
 [COLOR=#666666]904[/COLOR].293853760 [COLOR=#666666]=[/COLOR] [COLOR=#666666]970[/COLOR].978131968  boot/initrd.img.old                            [COLOR=#B8860B]2[/COLOR]

[COLOR=#666666]======================[/COLOR] sdf1/boot/grub/menu.lst [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]======================[/COLOR]

[COLOR=#008800]*# This Menu created with Universal USB Installer [https://www.pendrivelinux.com](https://www.pendrivelinux.com)*[/COLOR]
default [COLOR=#666666]0[/COLOR]
timeout [COLOR=#666666]30[/COLOR]
color NORMAL HIGHLIGHT HELPTEXT HEADING
[COLOR=#B8860B]foreground[/COLOR][COLOR=#666666]=[/COLOR]FFFFFF
[COLOR=#B8860B]background[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#666666]000000[/COLOR]
title Boot lubuntu-19.10-desktop-amd64
[COLOR=#AA22FF]set[/COLOR] [COLOR=#B8860B]ISO[/COLOR][COLOR=#666666]=[/COLOR]/lubuntu-19.10-desktop-amd64.iso
[COLOR=#AA22FF]set[/COLOR] [COLOR=#B8860B]CASPER[/COLOR][COLOR=#666666]=[/COLOR]/casper-rw
find --set-root %ISO%
map %ISO% [COLOR=#666666]([/COLOR]0xff[COLOR=#666666])[/COLOR]
[COLOR=#008800]*#CLUG*[/COLOR]
map --hook
root [COLOR=#666666]([/COLOR]0xff[COLOR=#666666])[/COLOR]
kernel /casper/vmlinuz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/preseed/lubuntu.seed noprompt [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper iso-scan/filename[COLOR=#666666]=[/COLOR]%ISO% quiet --
initrd /casper/initrd
title Boot lubuntu-19.10-desktop-amd64 [COLOR=#B8860B]acpi[/COLOR][COLOR=#666666]=[/COLOR]off
[COLOR=#AA22FF]set[/COLOR] [COLOR=#B8860B]ISO[/COLOR][COLOR=#666666]=[/COLOR]/lubuntu-19.10-desktop-amd64.iso
[COLOR=#AA22FF]set[/COLOR] [COLOR=#B8860B]CASPER[/COLOR][COLOR=#666666]=[/COLOR]/casper-rw
find --set-root %ISO%
map %ISO% [COLOR=#666666]([/COLOR]0xff[COLOR=#666666])[/COLOR]
[COLOR=#008800]*#CLUG*[/COLOR]
map --hook
root [COLOR=#666666]([/COLOR]0xff[COLOR=#666666])[/COLOR]
kernel /casper/vmlinuz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/preseed/lubuntu.seed noprompt [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper iso-scan/filename[COLOR=#666666]=[/COLOR]%ISO% quiet [COLOR=#B8860B]acpi[/COLOR][COLOR=#666666]=[/COLOR]off --
initrd /casper/initrd

[COLOR=#666666]====================[/COLOR] sdf1: Location of files loaded by [COLOR=#B8860B]Grub[/COLOR] [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]

            ?? [COLOR=#666666]=[/COLOR] ??             boot/grub/menu.lst                             [COLOR=#666666]1[/COLOR]
            ?? [COLOR=#666666]=[/COLOR] ??             vmlinuz                                        [COLOR=#666666]1[/COLOR]
            ?? [COLOR=#666666]=[/COLOR] ??             initrd                                         [COLOR=#B8860B]1[/COLOR]


[COLOR=#666666]=========[/COLOR] Devices which don't seem to have a corresponding hard [COLOR=#B8860B]drive[/COLOR] [COLOR=#666666]==========[/COLOR]

sdb sdc sdd [COLOR=#B8860B]sde[/COLOR] 


[COLOR=#666666]===============================[/COLOR] StdErr [COLOR=#B8860B]Messages[/COLOR] [COLOR=#666666]================================[/COLOR]

  /dev/sdb: open failed: No medium found
  /dev/sdc: open failed: No medium found
  /dev/sdd: open failed: No medium found
  /dev/sde: open failed: No medium found

Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would purge [COLOR=#666666]([/COLOR]in order to fix packages[COLOR=#666666])[/COLOR] and reinstall the grub-efi-amd64-signed of
sda5,
using the following options:        sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s  use-standard-efi-file    

Blockers in [COLOR=#AA22FF]**case**[/COLOR] of suggested repair: __________________________________________

The current session is in Legacy mode. Please reboot the computer, and use this software in an EFI session. This will [COLOR=#AA22FF]enable[/COLOR] this feature. For example, use a live-USB of Boot-Repair-Disk-64bit [COLOR=#666666]([/COLOR]www.sourceforge.net/p/boot-repair-cd[COLOR=#666666])[/COLOR], after making sure your BIOS is [COLOR=#AA22FF]set[/COLOR] up to boot USB in EFI mode. 

Advice in [COLOR=#AA22FF]**case**[/COLOR] of suggested repair: ____________________________________________

The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
Do you want to [COLOR=#AA22FF]**continue**[/COLOR]?

Final advice in [COLOR=#AA22FF]**case**[/COLOR] of suggested repair: ______________________________________

Please [COLOR=#AA22FF]**do**[/COLOR] not forget to make your BIOS boot on sda2/efi/****/shim****.efi [COLOR=#666666]([/COLOR]**** will be updated in the final message[COLOR=#666666])[/COLOR] file!

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, [COLOR=#AA22FF]**then**[/COLOR] [COLOR=#AA22FF]type[/COLOR] the following [COLOR=#AA22FF]command[/COLOR] in an admin [COLOR=#AA22FF]command[/COLOR] prompt:
bcdedit /set [COLOR=#666666]{[/COLOR]bootmgr[COLOR=#666666]}[/COLOR] path [COLOR=#BB6622]**\E**[/COLOR]FI[COLOR=#BB6622]**\***[/COLOR]***[COLOR=#BB6622]**\s**[/COLOR]him****.efi [COLOR=#666666]([/COLOR]**** will be updated in the final message[COLOR=#666666])[/COLOR]

The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
```

---

### Post by oldfred on 2020-05-07
Please use code tags if longer output from terminal or text.
Easy to add with Forum's advanced editor & # icon.

Even better with Boot-Repair, just post the link it provides.

Windows is in UEFI boot mode.
But you installed Ubuntu in BIOS boot mode, you need to convert to UEFI boot mode and can easily do that by rebooting Ubuntu installer in UEFI boot mode and running Boot-Repair to reinstall grub or the UEFI version of grub.

With UEFI, you should always be able to directly boot Windows from UEFI boot menu. Same set of keys to boot live installer flash drive. And since grub only boots working Windows and Windows turns fast start up back on with some updates, you will sometimes have to directly boot Windows to turn fast start up back off.

Make sure fast start up is off in Windows.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)


HP is not always the easiest to UEFI dual boot. Some have said that if you update HP's UEFI from HP it works better.
And you often have to use HP's UEFI to change boot order as it keeps resetting any changes using efibootmgr. Grub uses efibootmgr to change boot order & Ubuntu may boot once.
Some old HP have to set the fallback or hard drive entry to boot Ubuntu as "ubuntu" entry just is not allowed.

---

### Post by campol on 2020-05-07
[IMG]https://imgur.com/a/6HNGb5f[/IMG][IMG]https://imgur.com/a/6HNGb5f[/IMG]
>[COLOR=#000000]you need to convert to UEFI boot mode and can easily do that by rebooting Ubuntu installer in UEFI boot mode

[/COLOR]I can only boot from the USB from the legacy options

[https://imgur.com/a/6HNGb5f](https://imgur.com/a/6HNGb5f)


>[COLOR=#000000]you should always be able to directly boot Windows from UEFI boot menu[/COLOR]

As I said I can't do that anymore since I edited the bootmanager value with

[COLOR=#000000]bcdedit /set {bootmgr} path \EFI\lubuntu\grubx64.efi


[/COLOR]

---

### Post by oldfred on 2020-05-07
I do not know Windows, but thought that was just another entry in Windows BCD.

Can you not boot Windows and press f8 before it starts booting to get into its repair console.
Otherwise you have to use the Windows repair flash drive that it tells you to first make when booting Windows.
You can make that from any other Windows system of same 64 bit configuration if required, or download ISO and make new installer to use its repair.

It says USB hard drive is a boot option in UEFI choices?

---

### Post by campol on 2020-05-07
Thank you I managed to start windows through different means and now it does boot to windows. now my problem is to correctly set GRUB as the boot manager and be able to choose Windows and Lubuntu from it...

---

### Post by yancek on 2020-05-08
Did you try the option suggested by oldfred to select  USB hard drive is a boot option in UEFI?  You need to boot in UEFI mode to do an EFI install of Grub.  A legacy install of Lubuntu with Grub will not boot a windows EFI install.  This is explained in the Ubuntu documentation at the link below.

    [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2020-05-08
You need to boot Ubuntu installer in UEFI mode.
Add Boot-Repair and reinstall grub's UEFI version.

HP ubuntu entry may work once as grub uses efibootmgr to set boot order, but HP often resets it. Many with HP have said they could update UEFI and still then only change boot order using HP's UEFI settings. Some others have used rEFInd as boot manager or just always choose boot in UEFI menu.

---

### Post by campol on 2020-05-08
I updated the BIOS from 8.1 to v 8.19(2014) and still won't let me boot the USB from UEFI mode, only Legacy Mode as in the image [https://imgur.com/a/6HNGb5f](https://imgur.com/a/6HNGb5f) what are my options?

Is there a way to perform boot repair from Windows? as it is the only way I can boot UEFI mode

---

### Post by oldfred on 2020-05-08
My systems normally show USB flash drives as a hard drive.
What boots with your UEFI USB hard drive entry?

---

