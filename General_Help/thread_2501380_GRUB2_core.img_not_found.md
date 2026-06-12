---
title: "GRUB2 core.img not found"
date: 2024-10-04
forum: General Help
---

### Post by johnnormandavis on 2024-10-04
I've been using Ubuntu for years, but on this issue I might as well be a newbie. Please let me know if there's a more appropriate forum.
I can run Live from a USB stick. I ran boot-repair and got the following:
[https://paste.ubuntu.com/p/sxwZXQbmZZ/](https://paste.ubuntu.com/p/sxwZXQbmZZ/)

```
boot-repair-4ppa2081                                              [20241004_1722]

============================== Boot Info Summary ===============================


sda: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sda: /dev/sda already mounted or mount point busy.
       dmesg(1) may have more information after failed mount system call.


================================ 0 OS detected =================================


================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: Haswell-ULT Integrated Graphics Controller from Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 24.04.1 LTS, noble, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: A08 from Dell Inc.
The firmware seems EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).



============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________


Partitions info (1/3): _________________________________________________________


Partitions info (2/3): _________________________________________________________


Partitions info (3/3): _________________________________________________________


fdisk -l (filtered): ___________________________________________________________

Disk sda: 14.92 GiB, 16018046976 bytes, 31285248 sectors
Disk identifier: EED3DE8A-ACD3-4541-BA15-9014C007D874
        Start      End  Sectors  Size Type
sda1        64 12105119 12105056  5.8G Microsoft basic data
sda2  12105120 12115263    10144    5M EFI System
sda3  12115264 12115863      600  300K Microsoft basic data
sda4  12115968 31283199 19167232  9.1G Linux filesystem

parted -lm (filtered): _________________________________________________________

sda:16.0GB:scsi:512:512:gpt:Lexar USB Flash Drive:;
1:32.8kB:6198MB:6198MB::ISO9660:hidden, msftdata;
2:6198MB:6203MB:5194kB::Appended2:boot, esp;
3:6203MB:6203MB:307kB::Gap1:hidden, msftdata;
4:6203MB:16.0GB:9814MB:ext4::;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda    iso9660  2024-08-27-16-23-26-00                                                    Ubuntu 24.04.1 LTS amd64 
&#9500;&#9472;sda1 iso9660  2024-08-27-16-23-26-00               eed3de8a-acd3-4541-ba14-9014c007d874 Ubuntu 24.04.1 LTS amd64 ISO9660
&#9500;&#9472;sda2 vfat     3C53-CAEB                            eed3de8a-acd3-4541-ba17-9014c007d874 ESP                      Appended2
&#9500;&#9472;sda3                                               eed3de8a-acd3-4541-ba16-9014c007d874                          Gap1
&#9492;&#9472;sda4 ext4     478e5bf2-8463-4a01-9917-2b6e4933b5b6 dc899ed4-85e2-48f0-9de0-618e50f98499 writable                 

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/sda1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sda1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.

```

---

### Post by oldfred on 2024-10-04
Better to only post link to summary report.

But Report shows no internal drive(s). Just the USB flash drive live installer.

Does UEFI settings show drive correctly? If not shown, then no system will see drives.
If drives shown are they in AHCI mode, or something else like Intel RST or RAID?
You typically need AHCI, but have to install AHCI drivers into Windows if dual booting.

What brand/model system? What video card/chip?

---

### Post by johnnormandavis on 2024-10-04
The UEFI settings do not show the drive correctly. I fear the only issue is how completely fried it is.

This is an older Dell Latitude 3540 that should have been been put out to pasture long ago, I suppose.
Intel® Core&#8482; i5-4210U × 4
Intel® HD Graphics 4400 (HSW GT2)

Thanks for the reply.

---

### Post by oldfred on 2024-10-04
First thing to check is connections, both SATA & power.
Cable could be just loose or a bad cable. 

I have full install on external SSD and that has worked well for booting several of my systems.

---

