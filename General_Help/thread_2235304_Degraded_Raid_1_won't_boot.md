---
title: "Degraded Raid 1 won't boot"
date: 2014-07-20
forum: General Help
---

### Post by sebastien2 on 2014-07-20
My problem started when i removed a failed disk from my raid 1. The first reboot was fine but now I can't boot anymore. I can't even access GRUB menu, my PC keeps rebooting after the bios screen.

I can boot a LiveCD (USB) and tried to repair my MBR using boot-repair but it doesn't work.

Here are the boot info script result. The affected drive is /dev/sda (/dev/sdb is a data drive and can be ignored, /dev/sdc is the Ubuntu LiveCD).

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (mduuid/6e590dfbd061ed70f24b7b7b7b38534a)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (mduuid/6e590dfbd061ed70f24b7b7b7b38534a)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 58874 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/BOOT/grubx64.efi

md/1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

md/0: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount : /dev/md0 est déjà monté ou MDRaid/md/0 est occupé
mount : selon mtab, /dev/md0 est monté sur /media/ubuntu/5a9fbd0d-683d-42fb-a2ec-7283737336c8

md/2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 têtes, 63 secteurs/piste, 243201 cylindres, total 3907029168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 4096 octets

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63 3,890,878,739 3,890,878,677  fd Linux raid autodetect
/dev/sda2       3,890,890,750 3,907,028,991    16,138,242   5 Extended
/dev/sda5       3,890,890,752 3,907,028,991    16,138,240  fd Linux raid autodetect


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 têtes, 63 secteurs/piste, 30401 cylindres, total 488397168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   488,392,064   488,392,002  83 Linux


Drive: sdc _____________________________________________________________________

Disque /dev/sdc : 7756 Mo, 7756087296 octets
255 têtes, 63 secteurs/piste, 942 cylindres, total 15148608 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63    15,117,164    15,117,102   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       eac2aafb-4234-fc49-9701-baebaf8bd6be   ext2       casper-rw
/dev/md0         5a9fbd0d-683d-42fb-a2ec-7283737336c8   ext4       
/dev/md/0        5a9fbd0d-683d-42fb-a2ec-7283737336c8   ext4       
/dev/md1         edf27535-8979-455d-8b1a-d6a67a07a600   swap       
/dev/md/1        edf27535-8979-455d-8b1a-d6a67a07a600   swap       
/dev/md2         589c43f6-cfd7-416c-a414-b0685929df08   ext4       Raid 250 Go
/dev/md/2        589c43f6-cfd7-416c-a414-b0685929df08   ext4       Raid 250 Go
/dev/sda1        6e590dfb-d061-ed70-f24b-7b7b7b38534a   linux_raid_member pc-maison:0
/dev/sda5        36188cc0-122b-4515-c8e3-626c197e7b4b   linux_raid_member pc-maison:1
/dev/sdb1        dbd7da5f-bd15-5349-5081-3d8e113a0efe   linux_raid_member pc-maison:2
/dev/sdc1        1505-1E65                              vfat       UUI

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/md0         /media/ubuntu/5a9fbd0d-683d-42fb-a2ec-7283737336c8 ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

xz : (stdin): Les données compressées sont corrompues
xz : (stdin): Les données compressées sont corrompues
cat: /tmp/BootInfo-nFdIR70d/Tmp_Log: Aucun fichier ou dossier de ce type
  No volume groups found


```


Thanks for your help!

---

