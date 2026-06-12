---
title: "Need to config grub to also boot using MBR"
date: 2020-04-16
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2020-04-16
Currently I have a box that has a GTP partition table on a SSD with a BIOS_GRUB partition and a root partition, it also has a HDD with a MBR partition table that has /home, /var, and /mnt/storage
I need to move these drive into anohter box that is newer, but the BIOS on that box is crap and does not see the drives as boot-able so i need to have the MBR on the HDD handle the boot initialization process
i tried to fix it with my flash drive but ended up breaking grub on my flash drive and my command to fix it no longer works cause it predates efi booting

---

### Post by CelticWarrior on 2020-04-17
Are you sure "the BIOS on that box is crap"? And if new is it really BIOS? Anything from the last 8-10 years have UEFI, not BIOS and UEFI without Legacy/CSM mode enabled won't boot anything installed in "BIOS mode".

Better to just reinstall and also use GPT and UEFI everywhere instead of being stuck in the past century.

---

### Post by pqwoerituytrueiwoq on 2020-04-17
Sandy bridge based OEM desktop (pretty sure my sandy bridge laptop has no issues booting eufi)
the SSD is bootable, it works in other systems
the silly BIOS can't find the OS even when i make the SSD the only boot device

---

### Post by CelticWarrior on 2020-04-17
> **pqwoerituytrueiwoq said:**
> Sandy bridge based OEM desktop (pretty sure my sandy bridge laptop has no issues booting eufi)
the SSD is bootable, it works in other systems
the silly BIOS can't find the OS even when i make the SSD the only boot device


This 3 lines show that you didn't really understand what I commented before and you don't understand UEFI in general.

The suggestion was and still is to NOT insist in legacy mode, have all drives in GPT (great advantages) and reinstall in UEFI mode (huge advantages, especially for multi-booting).

---

### Post by pqwoerituytrueiwoq on 2020-04-17
On a modern system you can choose UEFI/CSM or UEFI, the existing install is in UEFI, but the other box is clearly CSM only as it does not detect the OS and tries to boot off a old invalid MBR on the HDD
it is not a boot priority issue, i removed the HDD from the boot-able drives in the BIOS and it can't find a OC

I know the BIOS_GRUB partition on a GPT does what the reserved space on a MBR parathion table does, on the BIOS_GRUB parathion is setup for UEFI and the MBR on the HDD has a old invalid config
SSD = /dev/sda GPT
* BIOS _GRUB
* /root
HDD = /dev/sdb MBR
* /home
* /var
* /mnt/storage

If i have both setup in a valid state it will be swap-able between both UEFI and pe-UEFI motherboard

The old box has a AMD A6-3500 (with UEFI support), the new box has a i5-2320 (no UEFI support)

---

### Post by oldfred on 2020-04-17
Not sure what you are trying?
Grub in the MBR of the HDD, would need the rest of grub & kernel in SSD to boot.

Or are you just trying to boot other system and copy data from MBR based HDD?

Boot Ubuntu live installer and run Boot-Repair. Post link to summary report.
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by CelticWarrior on 2020-04-17
> **pqwoerituytrueiwoq said:**
> On a modern system you can choose UEFI/CSM or UEFI, the existing install is in UEFI, but the other box is clearly CSM only as it does not detect the OS and tries to boot off a old invalid MBR on the HDD

Some system allow UEFI+Legacy, others only one or the other, and a few don't have CSM at all so the only mode is UEFI.
And if we nitpick the terminology - as I often do -  it makes no sense talking about [CSM]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#CSM_booting") if not in the context of UEFI. A "CSM only box" is oxymoronic. It's either BIOS or UEFI and if the latter it may or may not have CSM which is sort of "emulated BIOS" that allow booting an OS> in the same way as on legacy BIOS-based systems, by ignoring the partition table and relying on the content of a [boot sector]("https://en.wikipedia.org/wiki/Boot_sector").


> I know the BIOS_GRUB partition on a GPT does what the reserved space on a  MBR parathion table does, on the BIOS_GRUB parathion is setup for UEFI  and the MBR on the HDD has a old invalid config

First of all, MBR - Master Boot Record - is NOT a partition.
Secondly, **a 'bios_grub' IS the hallmark of a BIOS/Legacy/CSM installation in a GPT drive.** It's there instead of the MBR that doesn't exist in GPT, obviously. **It is NOT and CANNOT be "setup for UEFI"**. UEFI installations require a ESP - EFI System Partition - a small FAT32 partition typically at the beginning of the drive where the .efi files are written and where the firmware (UEFI) reads them from in order to boot. 


```
SSD = /dev/sda GPT
* BIOS _GRUB
* /root
HDD = /dev/sdb MBR
* /home
* /var
* /mnt/storage
```

Clearly no ESP (EFI partition) so this is completely wrong and very indicative of your confusion: > If i have both setup in a valid state it will be swap-able between both UEFI and pe-UEFI motherboard


Also,
> The old box has a AMD A6-3500 (with UEFI support), the new box has a i5-2320 (no UEFI support) 				
clearly indicates you still don't know what UEFI is. Pehaps you should start by reading the Wikipedia about [Unified Extensible Firmware Interface]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface") to finally understand some basic stuff:
[LIST]
[*]UEFI is what replaced BIOS a long time ago. Although many people and manufacturers still refer to UEFI as "BIOS" that's so wrong in so many ways. Maybe the goal was/is to avoid confusion but it clearly backfired in your case and many others. Hardly a day goes by without we needing to explain this same s... all over again.
[*]You have a Legacy ("BIOS") installation in a GPT drive because Ubuntu allows that (maybe it shouldn't?) unlike Windows that has strict requirements of MBR for BIOS or Legacy mode in UEFI and GPT for UEFI
[*]Yes, surely the AMD APU - A6-3500 - based machione has UEFI (there were no BIOS system with AMD APUs), not "UEFI support" which is just a dumb way to put it, and although the Intel i5-2320 - BTW, not really new, it's an old generation discontinued 7 years ago could be either BIOS or UEFI, it is very likely the latter and probably a very early and very broken UEFI implementation, reason why your LEGACY installation doesn't boot there.
[/LIST]

---

### Post by CelticWarrior on 2020-04-17
> **oldfred said:**
> Not sure what you are trying?
Grub in the MBR of the HDD, would need the rest of grub & kernel in SSD to boot.

Or are you just trying to boot other system and copy data from MBR based HDD?

@oldfed

It's much simpler that what it looks like at first glance. The problem is OP is confused and that confuses us. But it's quite simple: OP is trying to boot a previous installation in a new machine. But OP is convinced that installation is either UEFI or "UEFI/BIOS compatible". It isn't, it's likely a typical legacy mode installation in a GPT drive (with 'bios_grub' partition), in a UEFI machine (AMD APU based) that now wants to boot in an old i5 based machine from 2011 (so, I'm not sure it's UEFI or BIOS and if the former if it has CSM).

---

### Post by pqwoerituytrueiwoq on 2020-04-17
There is only 1 OS installed,
Just want the HDD's MBR to tell the BIOS to boot the SSD
I think this is what is the command i wanted
```

sudo grub-install --target=i386-pc --boot-directory=/boot/ /dev/sdb

```

that utility is how i managed to mess up my flash drive

My dad got the OEM PC as a upgrade a few years ago and never bothered to let me move his stuff over, he never let me upgrade him form 14.04 to 18.04, so i just put 20.04 on it (clean install, only /home was NOT formatted), who knows when i will find out if that command worked (current system access is over SSH)

what finally got him to let me update it was it started crashing when he put it under a light load (page scrolling or google street view) crashed seemed like OCP or something but when i got it in my room and fired up Unigine Heaven (sub 10FPS on low @ 1080p) and mprime small FFTs as the same time there is no problem, figured it was just a driver support and FF issues since the OS has been unsupported for so long, he is still having the issues after upgrading, so unless this is a issues with his power-cable/outlet IDK what it could be

```

~$ sudo parted -l
Model: ATA KINGSTON SV100S2 (scsi)
Disk /dev/sda: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  27.7GB  27.7GB  ext4         Root  boot, esp


Model: ATA WDC WD800AAJS-55 (scsi)
Disk /dev/sdb: 80.0GB <-- Yep that drive has been in use since he had a refurbished Pentium 4 based desktop
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  7518MB  7518MB  primary   ext4
 2      7518MB  80.0GB  72.5GB  extended
 5      7518MB  55.9GB  48.3GB  logical   ext4
 7      55.9GB  72.0GB  16.1GB  logical   ext4
 6      72.0GB  80.0GB  8053MB  logical   linux-swap(v1)

```
```
~$ sudo blkid
/dev/sdb6: UUID="fc2a810f-a518-404d-b273-cf64cd1926c6" TYPE="swap" PARTUUID="000736ab-06"
/dev/sda2: UUID="768ad1f3-919e-4c3f-bb49-13fdb5db3c10" TYPE="ext4" PARTLABEL="Root" PARTUUID="49e53765-a797-430a-a4e5-92dd2f312368"
/dev/sda1: PARTUUID="e6025fbb-cb32-42ae-9223-6059bf6fe296"
/dev/sdb1: UUID="b099b430-7bb9-4fe8-8879-523b917a4a51" TYPE="ext4" PARTUUID="000736ab-01"
/dev/sdb5: LABEL="Home" UUID="f157f3c4-e9fd-40aa-a1d4-0aa249333db7" TYPE="ext4" PARTUUID="000736ab-05"
/dev/sdb7: LABEL="WindowsVM" UUID="8d16ecdf-deae-4f68-ac1c-65352f2ae3e1" TYPE="ext4" PARTUUID="000736ab-07"
```
```
~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=768ad1f3-919e-4c3f-bb49-13fdb5db3c10 /               ext4    noatime,errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=f157f3c4-e9fd-40aa-a1d4-0aa249333db7 /home           ext4    defaults        0       2
# /var was on /dev/sdb1 during installation
UUID=b099b430-7bb9-4fe8-8879-523b917a4a51 /var            ext4    defaults        0       2
# Windows vb disk image
UUID=8d16ecdf-deae-4f68-ac1c-65352f2ae3e1 /mnt/Windows    ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=fc2a810f-a518-404d-b273-cf64cd1926c6 none            swap    sw              0       0
# /tmp was moved to RAM after installation
tmpfs                                     /tmp            tmpfs   defaults,noatime,mode=1777 0       0
```

---

