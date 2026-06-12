---
title: "my feisty jumps back and forth between sda and hdb!"
date: 2007-05-20
forum: General Help
---

### Post by manifoldronin on 2007-05-20
After upgrading to Feisty from Edgy, my harddrive and partitions were changed to /dev/sda*, and the dvd drive became /dev/scd0. A couple of days back I noticed they went back to /dev/hdb* and /dev/hdc.  After rebooting, they are now back to /dev/sda* and /dev/scd0.  What's going on?  Thanks.

---

### Post by rich.bradshaw on 2007-05-20
In Feisty, non-sata drives (previously hdx#) are handled by the SATA drivers, making them sdx#. Sounds like the old drivers are still in use sometimes... that shouldn't really happen though! Obviously! What's the output of

cat /etc/fstab

---

### Post by manifoldronin on 2007-05-20
The fstab looks like this.  Any thoughts?  Thanks.

# /etc/fstab: static file system information.
#
# <file system>                           <mount point>           <type>      <options>                    <dump>  <pass>
proc                                      /proc                   proc        defaults                     0       0
# /dev/hdb3
UUID=d50cd163-5303-4a9c-8995-8e4d5f937f72 /                       ext3        defaults,errors=remount-ro   0       1
# /dev/hdb1
UUID=22C47163C47139DD                     /win/c                  ntfs        ro,nls=utf8,umask=007,gid=46 0       2
# /dev/hdb5
UUID=455F-7F3A                            /win/e                  vfat        rw,umask=007,gid=46          0       2
# /dev/hdb4
UUID=1ebc9513-cebe-420e-88b2-ed9c1fe24d09 none                    swap        sw                           0       0
# /dev/hdb6
UUID=b4ff81b4-2c51-4ba9-ae85-ee505573487a /home                   ext3        defaults,errors=remount-ro   0       2
/dev/dvd                                  /media/dvd              udf,iso9660 user,noauto                  0       0
/dev/cdrom                                /media/cdrom            udf,iso9660 user,noauto                  0       0
#/dev/                                     /media/floppy0          auto        rw,user,noauto               0       0

---

### Post by Enverex on 2007-05-20
> **rich.bradshaw said:**
> In Feisty, non-sata drives (previously hdx#) are handled by the SATA drivers, making them sdx#.

Actually it's because the newer kernel switched over to SCSI for its IDE methods, not really anything to do with SATA.

---

### Post by manifoldronin on 2007-05-23
Well, I captured some log from two booting sequences, one leading to /dev/hdb, the other /dev/sda, and compared the two.  In the first case, the kernel seems to recognize the IDE controller:
```

 SIS5513: IDE controller at PCI slot 0000:00:02.5
 ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 16
 SIS5513: chipset revision 1
 SIS5513: not 100%% native mode: will probe irqs later
 SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
 Probing IDE interface ide0...

```

And in the second case, the kernel doesn't print the above section, instead it has this sequence:
```

 ata1.01: ata_hpa_resize 1: sectors = 320173056, hpa_sectors = 320173056
 ata1.01: ATA-7: Maxtor 6Y160P0, YAR41BW0, max UDMA/133
 ata1.01: 320173056 sectors, multi 16: LBA48 
 ata1.01: ata_hpa_resize 1: sectors = 320173056, hpa_sectors = 320173056
 ata1.01: configured for UDMA/133
 scsi1 : pata_sis
 ata2.00: ATAPI, max UDMA/100
 ata2.01: ATAPI, max MWDMA2
 ata2.00: configured for UDMA/100
 ata2.01: configured for PIO4
 scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6Y160P0   YAR4 PQ: 0 ANSI: 5
 ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
 ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 data 96 in
          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
 ata2: soft resetting port
 ata2.00: configured for UDMA/100
 ata2.01: configured for PIO4
 ata2: EH complete
 ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
 ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 data 96 in
          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
 ata2: soft resetting port
 ata2.00: configured for UDMA/100
 ata2.01: configured for PIO4
 ata2: EH complete
 ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
 ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 data 96 in
          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
 ata2: soft resetting port
 ata2.00: configured for UDMA/100
 ata2.01: configured for PIO4
 ata2: EH complete
 ata2.00: limiting speed to UDMA/66:PIO4
 ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
 ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 data 96 in
          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
 ata2: soft resetting port
 ata2.00: configured for UDMA/66
 ata2.01: configured for PIO4
 ata2: EH complete
 scsi scan: 96 byte inquiry failed.  Consider BLIST_INQUIRY_36 for this device
 scsi 1:0:0:0: CD-ROM            ASUS     DVD-E616P3       1.06 PQ: 0 ANSI: 5
 scsi 1:0:1:0: CD-ROM            PLEXTOR  CD-R   PX-W1210A 1.08 PQ: 0 ANSI: 5

```

Any thoughts on this?

---

### Post by manifoldronin on 2007-05-23
Mmm this is more serious than it had looked like - I just realized this is related to the dvd playback issue I've been having lately.  Looks like whenever the dvd drive is recognized as /dev/hdc, dvds play fine, whereas if it's mapped to /dev/scd0, I get "can't read from the source" error from kaffeine, or similar errors from other players.

I remember reading someone complaining about feisty fails to play dvd due to running sata driver over ide. Looks like not just me having this problem?

---

### Post by Locuss on 2007-05-26
I'm having the same issue as well. Is there a way to force the kernel to use the older drivers? Or, would using one of the older kernels do it?

---

### Post by hellmet on 2007-06-05
Same problem here [http://ubuntuforums.org/showthread.php?t=464822](http://ubuntuforums.org/showthread.php?t=464822)

---

### Post by manifoldronin on 2007-06-09
I suspect my problem is somewhat deeper - the harddrive jumps back and forth between hdb and sda between reboots.  And everytime it becomes sda, dvds don't play right.

---

### Post by DoktorSeven on 2007-06-10
This is what forced me to compile my own kernel for Feisty, leaving out the SCSI drivers.  I'm sure this isn't an issue for some systems but seems like older PATA drives suffer here.

---

