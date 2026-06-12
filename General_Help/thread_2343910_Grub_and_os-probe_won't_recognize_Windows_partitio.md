---
title: "Grub and os-probe won't recognize Windows partition after dist-upgrade"
date: 2016-11-20
forum: General Help
---

### Post by sean119 on 2016-11-20
I recently did a dist-upgrade on my system and after the upgrade was finished, my Windows partition was suddenly gone from my grub screen. I tried os-probe, but the Windows install isn't being recognized there either. 
fdisk -l output
> 
Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x2c0c660b

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdb1  *          2048     718847     716800   350M  7 HPFS/NTFS/exFAT
/dev/sdb2           718848 1137395711 1136676864   542G  7 HPFS/NTFS/exFAT
/dev/sdb3       1645402110 1952600063  307197954 146.5G  f W95 Ext'd (LBA)
/dev/sdb4       1952600064 1953521663     921600   450M 27 Hidden NTFS WinRE
/dev/sdb5       1645402112 1952600063  307197952 146.5G 83 Linux

Partition 3 does not start on physical sector boundary.
Partition table entries are not in disk order.


Disk /dev/sda: 489.1 GiB, 525112713216 bytes, 1025610768 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc6b8420b


/dev/sda is just an ssd I haven't used yet

/etc/grub.d/40_custom output

> 
#!/bin/sh
exec tail -n +3 $0
menuentry "Windows" {
        insmod ntfs
        set root=(hd0,1)
        search --no-floppy -fs-uuid --set A622172C2217014B
        chainloader +1
}
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

ls -l /dev/disk/by-uuid output
> 
lrwxrwxrwx 1 root root 10 Nov 20  2016 528E799F8E797C73 -> ../../sdb4
lrwxrwxrwx 1 root root 10 Nov 20  2016 5741063e-314f-4a7f-b9bd-2a05b89c6460 -> ../../sdb5
lrwxrwxrwx 1 root root 10 Nov 20  2016 A622172C2217014B -> ../../sdb2
lrwxrwxrwx 1 root root 10 Nov 20 16:53 B6F409E8F409AC25 -> ../../sdb1

Any suggestions? Thanks.

---

### Post by oldfred on 2016-11-20
If you added a new drive that is sda, then sda is probably (hd0), so you then have a command to boot from (hd0,1) or first partition on SSD.
Try editing on boot with e and see if hd1,1 works. Then you can permanently change.

Windows XP would not tolerate a change from sda, to sdb, or drive0 to drive1 without editing boot.ini. But Windows 7 and later use BCD and I think it internally use something like UUID, but not sure. If still issues you can try swapping drives.

Best to keep drives in SATA port order starting at SATA0 without skipping ports, and Windows on first drive.

---

### Post by sean119 on 2016-11-20
I changed the script to what you said, and when I tried to boot into 'Windows' on the grub screen, the prompt said, "erro: unspecified search type." and "no such partition". With what I had originally, I only got the first error. I don't think the error is related to the new drive because my Windows partition and Linux partition were working perfectly when I installed it. The breakage was the result of the dist-upgrade. Any other thoughts? Thanks for the reply by the way.

---

### Post by oldfred on 2016-11-20
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

