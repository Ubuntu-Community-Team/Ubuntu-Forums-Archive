---
title: "Ubuntu suddenly not recognized by BIOS anymore."
date: 2022-07-31
forum: General Help
---

### Post by Hibari on 2022-07-31
I was just restarting my system after a backup with Timeshift, and for some reason I'd like to know it doesn't seem to be recognized anymore.
I can get into the BIOS menu at boot, but there's no ubuntu option no matter how much I play with the settings.
BIOS is Aouros in case it matters.

Anyone know how I can get into recovery mode, at least?

---

### Post by grahammechanical on 2022-07-31
What happens when you switch on the computer? Knowing that would be helpful. Is this a dual boot? What version of Windows? If you run a Ubuntu live/try session you can load the Disks utility and get information about the partitions on the drive. What partitions do you see and what are they used for?

Regards

---

### Post by Hibari on 2022-07-31
> **grahammechanical said:**
> What happens when you switch on the computer? Knowing that would be helpful. Is this a dual boot? What version of Windows? If you run a Ubuntu live/try session you can load the Disks utility and get information about the partitions on the drive. What partitions do you see and what are they used for?

Regards

No dual boot, Ubuntu only.
When I switch it on, the BIOS logo appears and stays there for a long time (meaning a few minutes), then it tries to boot "Realtek 2.5 Gigabit Ethernet Controller", and eventually bring me back to the BIOS menu.

---

### Post by grahammechanical on 2022-07-31
Your BIOS cannot find a boot loader (in Ubuntu that would be GRUB). Please run a Ubuntu Live/Try session and install on it something called Boot-Repair. Do not using to repair the boot until after you have used it to create the boot summary report and upload to Pastebin. Put the link to the Pastebin in a post in this thread. Then we can examine the summary report and give you advice.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards

---

### Post by Hibari on 2022-07-31
> **grahammechanical said:**
> Your BIOS cannot find a boot loader (in Ubuntu that would be GRUB). Please run a Ubuntu Live/Try session and install on it something called Boot-Repair. Do not using to repair the boot until after you have used it to create the boot summary report and upload to Pastebin. Put the link to the Pastebin in a post in this thread. Then we can examine the summary report and give you advice.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards

Done, here you go.

[https://paste.ubuntu.com/p/kTXc7KGBgM/](https://paste.ubuntu.com/p/kTXc7KGBgM/)

---

### Post by Hibari on 2022-07-31
In case anyone can't access the link:

```
boot-repair-4ppa200                                              [20220731_1219]

============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (hd0,msdos1)/boot/grub. It also embeds following components:
    
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

md/imsm0: ______________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 


================================ 0 OS detected =================================


================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GA104 [GeForce RTX 3070] from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: F4 PI(5.17) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled - SecureBoot disabled - Please report this message to [email]boot.repair@gmail.com[/email].
BootCurrent: 0005
Timeout: 2 seconds
BootOrder: 0005,0006,0007,0004,0000
Boot0000* Windows Boot Manager	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0004* ubuntu	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0005* Realtek PXE B06 D00	BBS(Network,,0x0)..BO
Boot0006* UEFI: Netac, Partition 1	PciRoot(0x0)/Pci(0x14,0x0)/USB(24,0)/HD(1,MBR,0x8ab2c46,0x800,0x73f9800)..BO
Boot0007* Netac	BBS(HD,,0x0)..BO


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme1n1	: notGPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, no-os,	no-wind,	2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________


Partitions info (2/3): _________________________________________________________


Partitions info (3/3): _________________________________________________________


fdisk -l (filtered): ___________________________________________________________

Disk nvme1n1: 27.25 GiB, 29260513280 bytes, 57149440 sectors
Disk sda: 57.99 GiB, 62264442880 bytes, 121610240 sectors
Disk identifier: 0x08ab2c46
      Boot Start       End   Sectors Size Id Type
sda1  *     2048 121610239 121608192  58G  c W95 FAT32 (LBA)

parted -lm (filtered): _________________________________________________________

sda:62.3GB:scsi:512:512:msdos:Netac OnlyDisk:;
1:1049kB:62.3GB:62.3GB:fat32::boot, lba;
nvme1n1:29.3GB:nvme:512:512:unknown:INTEL HBRPEKNX0203AO:;

blkid (filtered): ______________________________________________________________

NAME    FSTYPE          UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                           
&#9492;&#9472;sda1  vfat            15EF-0E46                            08ab2c46-01                          UBUNTU 22_0 
nvme1n1 isw_raid_member                                                                                       
&#9492;&#9472;md127                                                                                                       

Mount points (filtered): _______________________________________________________

                       Avail Use% Mounted on
/dev/sda1              54.6G   6% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sda1              vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

====================== sda1/boot/grub/grub.cfg (filtered) ======================

Try or Install Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory

==================== sda1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown BootLoader on md/imsm0




=================== blkid (filtered) before raid activation ====================

/dev/nvme1n1: TYPE="isw_raid_member"
/dev/sda1: LABEL="UBUNTU 22_0" UUID="15EF-0E46" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="08ab2c46-01"


==================================== dmraid ====================================

dmraid -si -c
no block devices found
dmraid -ay:
no block devices found
dmraid -sa -c:
no block devices found


==================================== mdadm =====================================
mdadm --assemble --scan

mdadm --detail --scan
ARRAY /dev/md/imsm0 metadata=imsm UUID=0b664042:4aa18842:08590f76:9e8b9278


Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.

```

---

### Post by tea for one on 2022-07-31
[COLOR="#0000FF"]Line 81[/COLOR] - nvme1n1:29.3GB:nvme:512:512:unknown:INTEL HBRPEKNX0203AO

Is the device above Intel Optane RST?

---

### Post by Hibari on 2022-07-31
> **tea for one said:**
> [COLOR=#0000FF]Line 81[/COLOR] - nvme1n1:29.3GB:nvme:512:512:unknown:INTEL HBRPEKNX0203AO
 
Is the device above Intel Optane RST?

I genuinely don't know what that is, my disk is much bigger than 29.3GB so it's not that.

---

### Post by tea for one on 2022-07-31
I suspect that you have more than one disk.

Can you access the UEFI set up (i.e. BIOS) and see if you can find Chipset Sata Mode (or similar phrase)
Is the setting AHCI or RAID?

---

### Post by Hibari on 2022-07-31
> **tea for one said:**
> I suspect that you have more than one disk.

Can you access the UEFI set up (i.e. BIOS) and see if you can find Chipset Sata Mode (or similar phrase)
Is the setting AHCI or RAID?

There should only be one disk, I disconnected the external (UBS) HDD just in case it was causing trouble.
The only SATA related setting I can find is "SATA Controllers(s)", which is currently set on Disable.

---

### Post by tea for one on 2022-07-31
Sata controller set to Disable?
Should it not be enabled?

[COLOR="#0000FF"]Line 30[/COLOR] - 0 (zero) OS detected 
[COLOR="#0000FF"]Line 88[/COLOR] - nvme1n1 isw_raid_member

I was trying to establish if you had RAID but you say that you only have one disk?
Only one disk is found by boot-repair but it doesn't contain the OS.
This disk is smaller than your main disk?

In post no.1, you mentioned Timeshift.
Is your backup recent?
Is it restorable?

Suggestion:-
Set sata to enabled, remove usb extraneous drives and peripherals and run boot-repair again from a live session.

---

### Post by Hibari on 2022-07-31
There is an unmarked "ubuntu" boot option available in "easy mode" only, but putting it first does nothing...

---

### Post by Hibari on 2022-07-31
> **tea for one said:**
> Sata controller set to Disable?
Should it not be enabled?

[COLOR=#0000FF]Line 30[/COLOR] - 0 (zero) OS detected 
[COLOR=#0000FF]Line 88[/COLOR] - nvme1n1 isw_raid_member

I was trying to establish if you had RAID but you say that you only have one disk?
Only one disk is found by boot-repair but it doesn't contain the OS.
This disk is smaller than your main disk?

In post no.1, you mentioned Timeshift.
Is your backup recent?
Is it restorable?

Suggestion:-
Set sata to enabled, remove usb extraneous drives and peripherals and run boot-repair again from a live session.

I do not have RAID since I only have one disk, I temporarily enabled it on boot while trying to fix this, though. 
My main/only disk is 1TB, not sure why it is showing this instead.

More info:
- The timeshift backup is really recent but is on the main disk I cannot access.
- There is another one made with ubuntu-backup on an external disk, not sure how useful that could be.

---

### Post by mattbach on 2022-08-01
I know on the surface pro UEFI they insert a kind of pointer to the boot sectors of your operating systems.

I have had this go missing when I had a battery failure and had to use grub to reupload to the bios its locations for startup files and such.




[https://github.com/matthewJamesAbbott/](https://github.com/matthewJamesAbbott/)

---

### Post by Hibari on 2022-08-01
> **mattbach said:**
> I know on the surface pro UEFI they insert a kind of pointer to the boot sectors of your operating systems.

I have had this go missing when I had a battery failure and had to use grub to reupload to the bios its locations for startup files and such.


Is there a guide on how to do that somewhere?

---

