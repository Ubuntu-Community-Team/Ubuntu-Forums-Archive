---
title: "Ubuntu partition not recognized anymore."
date: 2022-07-31
forum: General Help
---

### Post by Hibari on 2022-07-31
I have no clue how it happened, but apparently my system does not recognize the Ubuntu partitions anymore, and it only shows one mysterious 29.3GB partition instead of the full 1TB.

Tried running boot repair via livecd, but there's no actual repair option, only the bootinfo one.
I have a backup so I could consider a reinstall, yet I can't even do that because the system does not see the disk I'm supposed to install it on.

What's going on?

Here's the BootInfo, by the way:

```
boot-repair-4ppa200                                              [COLOR=#666666][[/COLOR]20220801_0015[COLOR=#666666]][/COLOR]

[COLOR=#666666]==============================[/COLOR] Boot Info [COLOR=#B8860B]Summary[/COLOR] [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> No boot loader is installed in the MBR of /dev/nvme1n1.
 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v2.00[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector [COLOR=#666666]1[/COLOR] of 
    the same hard drive [COLOR=#AA22FF]**for**[/COLOR] core.img. core.img is at this location and looks 
    [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR]hd0,msdos1[COLOR=#666666])[/COLOR]/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi


[COLOR=#666666]================================[/COLOR] [COLOR=#666666]0[/COLOR] OS [COLOR=#B8860B]detected[/COLOR] [COLOR=#666666]=================================[/COLOR]


[COLOR=#666666]================================[/COLOR] Host/Hardware [COLOR=#666666]=================================[/COLOR]

CPU architecture: [COLOR=#666666]64[/COLOR]-bit
Video: GA104 [COLOR=#666666][[/COLOR]GeForce RTX [COLOR=#666666]3070[/COLOR][COLOR=#666666]][/COLOR] from NVIDIA Corporation
Live-session OS is Ubuntu [COLOR=#666666]64[/COLOR]-bit [COLOR=#666666]([/COLOR]Ubuntu [COLOR=#666666]22[/COLOR].04 LTS, jammy, x86_64[COLOR=#666666])[/COLOR]

[COLOR=#666666]=====================================[/COLOR] [COLOR=#B8860B]UEFI[/COLOR] [COLOR=#666666]=====================================[/COLOR]

BIOS/UEFI firmware: F4 PI[COLOR=#666666]([/COLOR][COLOR=#666666]5[/COLOR].17[COLOR=#666666])[/COLOR] from American Megatrends Inc.
The firmware is EFI-compatible, and is [COLOR=#AA22FF]set[/COLOR] in EFI-mode [COLOR=#AA22FF]**for**[/COLOR] this live-session.
SecureBoot disabled - SecureBoot disabled - Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL].
BootCurrent: [COLOR=#666666]0005[/COLOR]
Timeout: [COLOR=#666666]2[/COLOR] seconds
BootOrder: [COLOR=#666666]0005[/COLOR],0000,0004
Boot0000* Windows Boot Manager    VenHw[COLOR=#666666]([/COLOR]99e275e7-75a0-4b37-a2e6-c5385e6c00cb[COLOR=#666666])[/COLOR]WINDOWS.........x...B.C.D.O.B.J.E.C.T.[COLOR=#666666]=[/COLOR].[COLOR=#666666]{[/COLOR].9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.[COLOR=#666666]}[/COLOR]....................
Boot0004* ubuntu    VenHw[COLOR=#666666]([/COLOR]99e275e7-75a0-4b37-a2e6-c5385e6c00cb[COLOR=#666666])[/COLOR]
Boot0005* UEFI: Netac, Partition [COLOR=#666666]1[/COLOR]    PciRoot[COLOR=#666666]([/COLOR]0x0[COLOR=#666666])[/COLOR]/Pci[COLOR=#666666]([/COLOR]0x14,0x0[COLOR=#666666])[/COLOR]/USB[COLOR=#666666]([/COLOR][COLOR=#666666]24[/COLOR],0[COLOR=#666666])[/COLOR]/HD[COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR],MBR,0x8ab2c46,0x800,0x73f9800[COLOR=#666666])[/COLOR]..BO


[COLOR=#666666]=============================[/COLOR] Drive/Partition [COLOR=#B8860B]Info[/COLOR] [COLOR=#666666]=============================[/COLOR]

Disks info: ____________________________________________________________________


Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________


Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]2[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________


Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]3[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________


fdisk -l [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ___________________________________________________________

Disk nvme1n1: [COLOR=#666666]27[/COLOR].25 GiB, [COLOR=#666666]29260513280[/COLOR] bytes, [COLOR=#666666]57149440[/COLOR] sectors
Disk sda: [COLOR=#666666]57[/COLOR].99 GiB, [COLOR=#666666]62264442880[/COLOR] bytes, [COLOR=#666666]121610240[/COLOR] sectors
Disk identifier: 0x08ab2c46
      Boot Start       End   Sectors Size Id Type
sda1  *     [COLOR=#666666]2048[/COLOR] [COLOR=#666666]121610239[/COLOR] [COLOR=#666666]121608192[/COLOR]  58G  c W95 FAT32 [COLOR=#666666]([/COLOR]LBA[COLOR=#666666])[/COLOR]

parted -lm [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: _________________________________________________________

sda:62.3GB:scsi:512:512:msdos:Netac OnlyDisk:;
[COLOR=#666666]1[/COLOR]:1049kB:62.3GB:62.3GB:fat32::boot, lba;
nvme1n1:29.3GB:nvme:512:512:unknown:INTEL HBRPEKNX0203AO:;

blkid [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ______________________________________________________________

NAME    FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                    
&#9492;&#9472;sda1  vfat     15EF-0E46                            08ab2c46-01                          UBUNTU 22_0 
nvme1n1                                                                                                

Mount points [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: _______________________________________________________

                       Avail Use% Mounted on
/dev/sda1              [COLOR=#666666]54[/COLOR].6G   [COLOR=#666666]6[/COLOR]% /cdrom

Mount options [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ______________________________________________________

/dev/sda1              vfat            ro,noatime,fmask[COLOR=#666666]=[/COLOR][COLOR=#666666]0022[/COLOR],dmask[COLOR=#666666]=[/COLOR][COLOR=#666666]0022[/COLOR],codepage[COLOR=#666666]=[/COLOR][COLOR=#666666]437[/COLOR],iocharset[COLOR=#666666]=[/COLOR]iso8859-1,shortname[COLOR=#666666]=[/COLOR]mixed,errors[COLOR=#666666]=[/COLOR]remount-ro

[COLOR=#666666]======================[/COLOR] sda1/boot/grub/grub.cfg [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]======================[/COLOR]

Try or Install Ubuntu
Ubuntu [COLOR=#666666]([/COLOR]safe graphics[COLOR=#666666])[/COLOR]
OEM install [COLOR=#666666]([/COLOR][COLOR=#AA22FF]**for**[/COLOR] manufacturers[COLOR=#666666])[/COLOR]
Boot from next volume
UEFI Firmware Settings
Test [COLOR=#B8860B]memory[/COLOR]

[COLOR=#666666]====================[/COLOR] sda1: Location of files loaded by [COLOR=#B8860B]Grub[/COLOR] [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]
            ?? [COLOR=#666666]=[/COLOR] ??             boot/grub/grub.cfg                             [COLOR=#666666]1[/COLOR]



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.
```

---

### Post by oldfred on 2022-07-31
Please use code tags for terminal output. With Boot-Repair better to just post link to Summary Report that it gives.
How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

You are not showing drive.
Did you do an UEFI update? You may not even see it if run with other updates.
Double check UEFI settings. An UEFI update resets many settings to defaults.
Check Secure Boot, Drive as AHCI and any others you changed. I have a list of 7 settings I have to redo one one system after UEFI update.

---

### Post by Hibari on 2022-08-01
> **oldfred said:**
> You are not showing drive.
 
I know, but can't figure out why.

> **oldfred said:**
> Did you do an UEFI update? You may not even see it if run with other updates.
Double check UEFI settings. An UEFI update resets many settings to defaults.
Check Secure Boot, Drive as AHCI and any others you changed. I have a list of 7 settings I have to redo one one system after UEFI update.

I did not update it, although of course it might not have notified me.
Tried messing around with option hoping it would make the drive appear, but nothing.

Here's some of the current settings, just in case:

CSM Support - Disabled
Secure Boot Mode - Standard (which means disabled, as far as I understand)
Vt-d - Enabled
SATA Controller(s) - Disabled
UEFI Network Stack - Enabled
IPv4/6 PXE/HTTP Support - Disabled
Legacy USB Support - Enabled
XHCI Hand-off - Enabled
USB Mass Storage Driver Support - Enabled
SATA Mode Selection - AHCI
Intel PTT - Enabled
SGX - Enabled
3DMark01 Enhancement - Disabled
Security Device Support - Disable
Fast Boot - Disable Link
Windows 10 Features - Other OS
CSM Support - Disabled
Secure Boot - Disable

---

### Post by tea for one on 2022-08-01
Enable SATA Controller
Disable Intel PTT (Platform Trust Technology)
Disable SGX

Any good?

---

### Post by Hibari on 2022-08-01
> **tea for one said:**
> Enable SATA Controller
Disable Intel PTT (Platform Trust Technology)
Disable SGX

Any good?

Unfortunately, no.

I tried installing Ubuntu in the mysterious partition and that worked, yet I still cannot access the rest of the disk, maybe it's dying? I hope not...

---

