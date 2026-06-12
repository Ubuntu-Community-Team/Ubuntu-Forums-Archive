---
title: "Missing HDD"
date: 2019-06-06
forum: General Help
---

### Post by h4mm3r0g0d on 2019-06-06
So I have a buddies computer that the hard drive doesn't seem to be working correctly. I plug it into my computer's sata port and it shows up in bios but it reads as a 4gb drive even though it's a 3tb drive. When I boot into linux it doesn't see the hard drive at all.

```
sudo fdisk -l
Disk /dev/sda: 119.2 GiB, 128035676160 bytes, 250069680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe700e72d

Device     Boot  Start       End   Sectors   Size Id Type
/dev/sda1  *      2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2       206848 250066943 249860096 119.1G  7 HPFS/NTFS/exFAT


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe6dbf8f6

Device     Boot     Start        End   Sectors   Size Id Type
/dev/sdb1            2048  976564547 976562500 465.7G  7 HPFS/NTFS/exFAT
/dev/sdb2       976566270 1953523711 976957442 465.9G  5 Extended
/dev/sdb5       976566272 1953523711 976957440 465.9G 83 Linux


```
Shows my 2 normal drives but not the 3rd drive. 
It shows up in my bios as sata3_5.

```
dmesg | grep ata
[    0.000000] Memory: 8017940K/8344332K available (9093K kernel code, 1667K rwdata, 3820K rodata, 2236K init, 2364K bss, 326392K reserved, 0K cma-reserved)
[    0.276800] libata version 3.00 loaded.
[    1.528369] acpi_cpufreq: overriding BIOS provided _PSD data
[    1.530424] Write protecting the kernel read-only data: 14336k
[    1.595638] scsi host0: pata_atiixp
[    1.595800] scsi host1: pata_atiixp
[    1.595841] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.595842] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.605987] ata3: SATA max UDMA/133 abar m1024@0xfe20b000 port 0xfe20b100 irq 19
[    1.605989] ata4: SATA max UDMA/133 abar m1024@0xfe20b000 port 0xfe20b180 irq 19
[    1.605990] ata5: SATA max UDMA/133 abar m1024@0xfe20b000 port 0xfe20b200 irq 19
[    1.605992] ata6: SATA max UDMA/133 abar m1024@0xfe20b000 port 0xfe20b280 irq 19
[    1.765148] ata1.00: failed to read native max address (err_mask=0x1)
[    1.765149] ata1.00: HPA support seems broken, skipping HPA handling
[    1.765152] ata1.00: ATA-8: ST3000DM001, CC27, max UDMA/133
[    1.765153] ata1.00: 8089950 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.765158] ata1.00: limited to UDMA/33 due to 40-wire cable
[    1.765575] ata1.00: failed to set xfermode (err_mask=0x1)
[    1.921307] ata5: SATA link down (SStatus 0 SControl 300)
[    1.925104] ata6: SATA link down (SStatus 0 SControl 300)
[    2.081702] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.081723] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.082819] ata4.00: ATA-8: Hitachi HDS721010CLA332, JP4OA3MA, max UDMA/133
[    2.082820] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.083975] ata4.00: configured for UDMA/133
[    2.096731] ata3.00: ATA-8: ADATA SP900, 5.2.2, max UDMA/133
[    2.096732] ata3.00: 250069680 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.108455] ata3.00: configured for UDMA/133
[    7.154545] ata1.00: failed to set xfermode (err_mask=0x1)
[    7.154549] ata1.00: limiting speed to UDMA/33:PIO3
[   12.530442] ata1.00: failed to set xfermode (err_mask=0x1)
[   12.530445] ata1.00: disabled
[   13.065604] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)

```

Any suggestions on what could be the problem besides a completely fried drive? It was working fine the day before then all the games on it wouldn't play because windows magically lost the drive. No error messages, power surges, restarts or anything before the drive basically disconnected itself. Tried to restart the computer again the bios still shows the drive but wouldn't boot into that computers windows because the bootmgr was on this drive.

---

### Post by cruzer001 on 2019-06-06
What about doing a smart test on it?

[https://help.ubuntu.com/stable/ubuntu-help/disk-check.html.en](https://help.ubuntu.com/stable/ubuntu-help/disk-check.html.en)

---

### Post by h4mm3r0g0d on 2019-06-06
It doesn't show up anywhere to do the SMART test

---

### Post by oldfred on 2019-06-06
How are you connecting drive?
limited to UDMA/33 due to 40-wire cable

That is often the DVD cable for the old PATA type connection, and has not been used for HDD forever. 
If PATA use the newer 80 conduction cable, with blue end.

[https://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](https://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)

---

