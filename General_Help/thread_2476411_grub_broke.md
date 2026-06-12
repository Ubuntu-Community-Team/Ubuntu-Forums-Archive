---
title: "grub broke"
date: 2022-06-25
forum: General Help
---

### Post by Old Jimma on 2022-06-25
Hello Ubuntuers:

Grub broke when I was trying to install 20.04.4 on a Lenovo T420  Laptop. I bought the laptop used/refurbished about 6 months ago with Win10 installed. I think that the laptop was manufactured sometime between 2005 and 2011... not sure about that, howver.

I tried to repair the t grub... but it failed. I'm ot sure why. Perhaps something about BIOS vs UEFI mode. I don't know what that's about.

I really don't know how to fix this, and will be very grateful for help from people on Ubuntu forums.

Thank you,


Old Jimma

---

### Post by oldfred on 2022-06-25
It says 2011 when first released, but with Second gen i-series Intel chips.
That should be early UEFI, but UEFI was not really used much until 2012? 
And vendors still today call UEFI as BIOS, so any descriptions may not be definitive.

How much RAM? if on lower end, may be better with lighter weight flavor.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

I like Kubuntu which is more middle weight but found it still ran on my old 2006 1.5GB laptop where Ubuntu would not install. Only server would install to it, otherwise.

You need to review UEFI/BIOS settings. May have to download manual from vendors site.

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you want to fully document the specs. Link also has some details on how to use.
UbuntuForums 'system-info' Script
[https://ubuntuforums.org/showthread.php?t=2475931](https://ubuntuforums.org/showthread.php?t=2475931)

---

### Post by Old Jimma on 2022-06-25
Thanks for your reply oldfred. I'll get on it right away and report back soon.

---

### Post by Old Jimma on 2022-06-25
Hi oldfred,,

Here is the pastebin... I have no idea what it means!

```

boot-repair-4ppa200                                              [20220625_1730]

============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

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


================================ 1 OS detected =================================

OS#1:   Ubuntu 22.04 LTS on sda5

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GF119M [Quadro NVS 4200M] 2nd Generation Core Processor Family Integrated Graphics Controller from NVIDIA Corporation Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04.3 LTS, focal, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 83ET46WW (1.16 )(1.16) from LENOVO
The firmware seems EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).



============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : notGPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda5    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios

Partitions info (2/3): _________________________________________________________

sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda2    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda5    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda5    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 111.81 GiB, 120034123776 bytes, 234441648 sectors
Disk identifier: 0x8b893eb5
      Boot   Start       End   Sectors   Size Id Type
sda1          2048   1050623   1048576   512M  b W95 FAT32
sda2  *    1050624   2101247   1050624   513M ef EFI (FAT-12/16/32)
sda3       2103294 234440703 232337410 110.8G  5 Extended
sda5       2103296 234440703 232337408 110.8G 83 Linux
Disk sdb: 3.75 GiB, 4007657472 bytes, 7827456 sectors
Disk identifier: 0x2cf4ba3a
      Boot   Start     End Sectors  Size Id Type
sdb1  *          0 5999871 5999872  2.9G  0 Empty
sdb2       5271500 5279499    8000  3.9M ef EFI (FAT-12/16/32)
sdb3       6000640 7827455 1826816  892M 83 Linux

parted -lm (filtered): _________________________________________________________

sda:120GB:scsi:512:512:msdos:ATA KINGSTON SH103S3:;
1:1049kB:538MB:537MB:fat32::;
2:538MB:1076MB:538MB:fat32::boot, esp;
3:1077MB:120GB:119GB:::;
5:1077MB:120GB:119GB:ext4::;
sdb:4008MB:scsi:512:512:unknown:Memorex TRAVELDRIVE 005B:;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda                                                                                                                
&#9500;&#9472;sda1 vfat     1EB3-46F8                            8b893eb5-01                                                   
&#9500;&#9472;sda2 vfat     2AD8-4FF6                            8b893eb5-02                                                   
&#9500;&#9472;sda3                                               8b893eb5-03                                                   
&#9492;&#9472;sda5 ext4     2e254683-2e2c-4857-aba6-f4d0afcb789e 8b893eb5-05                                                   
sdb    iso9660  2021-08-19-11-03-38-00                                                    Ubuntu 20.04.3 LTS amd64 
&#9500;&#9472;sdb1 iso9660  2021-08-19-11-03-38-00               2cf4ba3a-01                          Ubuntu 20.04.3 LTS amd64 
&#9500;&#9472;sdb2 vfat     54C5-9C6C                            2cf4ba3a-02                                                   
&#9492;&#9472;sdb3 ext4     f7abdc6f-b41e-4f87-958e-f6f7d36ef989 2cf4ba3a-03                          writable                 

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/disk/by-label/writable[/install-logs-2022-06-25.0/crash] 797.7M   0% /var/crash
/dev/disk/by-label/writable[/install-logs-2022-06-25.0/log]   797.7M   0% /var/log
/dev/sda2                                                     505.8M   1% /mnt
/dev/sdb1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/disk/by-label/writable[/install-logs-2022-06-25.0/crash] ext4            rw,relatime
/dev/disk/by-label/writable[/install-logs-2022-06-25.0/log]   ext4            rw,relatime
/dev/sda1                                                     vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda2                                                     vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda2                                                     vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda5                                                     ext4            rw,relatime
/dev/sdb1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048

===================== sda2/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 2e254683-2e2c-4857-aba6-f4d0afcb789e root hd0,msdos5 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
sda5,
using the following options:  sda2/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups

Blockers in case of suggested repair: __________________________________________

 The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode. This will enable this feature.

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04 LTS entry (sda2/efi/****/grub****.efi (**** will be updated in the final message) file) !
The boot of your PC is in BIOS-compatibility/CSM/Legacy mode. You may want to retry after changing it to UEFI mode.

```

---

### Post by oldfred on 2022-06-25
If posting longer text or code, please use Code Tags.
Easy to add with Forum's Go Advanced editor and # icon.
[https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

The pastebin side should have been offered as an upload of the report when you ran it. It makes it easier to review as I do not have to scroll up  & down to review & comment.

Report did not show /etc/fstab?
That would show if install is really UEFI or BIOS as you have both shown. A BIOS boot in MBR and UEFI boot in ESP - efi system partition. Only one of those will work and that will depend on how you boot install. That may be an UEFI setting for default boot, either UEFI or BIOS/CSM/Legacy depending on which way install is actually configured. 

If using UEFI, much better to use gpt as UEFI highly recommends it.
I have used gpt with BIOS also, but then you need a tiny 1 or 2MB unformatted partition with bios_grub flag. For a while when converting from BIOS boot to UEFI boot I would have both the ESP & bios_grub partitions on my drives.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)

---

### Post by Old Jimma on 2022-06-25
Hello oldfred,

I followed the instructions. Thank you.

Basically, all I had to do was to 
[LIST]
[*]boot to Ubuntu 20.04.3 on a USB,
[*]select "Try Ubuntu,"
[*]then, click on Install Ubuntu.
[*]
[/LIST]

At the end of the install, the installation seems to install grub.

I was luck to have found my old black and orange "good luck USB" that I turned into a fishing lure a few years ago... caught alot of big trout with it. Had to dig down into my fishing kit to find it. It worked well ok, although  I had to scrape a few scales off  of it.

I'll put it back in my fishing kit, so I know where to find it next time I have a problem like this.

Best, and thanks!

Old Jimma from the Old Country

---

