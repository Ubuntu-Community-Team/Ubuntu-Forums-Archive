---
title: "PATA harddisk performance problems"
date: 2008-06-06
forum: General Help
---

### Post by ctrlER on 2008-06-06
Hi.
I have a Maxtor 6L300R0 and it seems that its performance is not what it should be.

As you can see, it takes 122 seconds to cat a 888 MB file to /dev/null, that gives a speed of about 7 Mbyte/sec which is really low especially considering that hdparm shows it can do 61 MByte/sec.
I tried with other files and the speed was about the same.

```
ctrler@jupiter:~/Media/Jogos$ time cat Dragon.Ball.AF-PS2_NTSC_DVDFull\(2007\).tar > /dev/null

real    2m2.626s
user    0m0.050s
sys     0m1.050s
ctrler@jupiter:~/Media/Jogos$
```


Here are the results from hdparm -tT /dev/sda, the seem normal, 61 MB/sec is very good.

```
ctrler@jupiter:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1728 MB in  2.00 seconds = 863.86 MB/sec
 Timing buffered disk reads:  186 MB in  3.03 seconds =  61.36 MB/sec
ctrler@jupiter:~$

```

Some aditional info:

```
ctrler@jupiter:~/Media/Jogos$ sudo hdparm -i /dev/sda                           
/dev/sda:

 Model=Maxtor 6L300R0                          , FwRev=BAH41G10, SerialNo=L62E71HG
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=586114704
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

ctrler@jupiter:~/Media/Jogos$


```

```
ctrler@jupiter:~/Media/Jogos$ uname -a
Linux jupiter 2.6.24-18-server #1 SMP Wed May 28 21:25:52 UTC 2008 i686 GNU/Linux

```

```
[   40.902895] scsi1 : ata_piix
[   40.903863] ata1: PATA max UDMA/100 cmd 0xd480 ctl 0xd400 bmdma 0xcc00 irq 20
[   40.903866] ata2: PATA max UDMA/100 cmd 0x8f0 ctl 0x8f8 bmdma 0xcc08 irq 20
[   41.073672] ata1.00: ATA-7: Maxtor 6L300R0, BAH41G10, max UDMA/133
[   41.073677] ata1.00: 586114704 sectors, multi 16: LBA48
[   41.113205] ata1.00: configured for UDMA/100
[   41.113249] ata2: port disabled. ignoring.
[   41.113384] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6L300R0   BAH4 PQ: 0 ANSI: 5
[   41.113456] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   41.113490] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   41.113527] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   41.113573] scsi2 : ata_piix
[   41.113614] scsi3 : ata_piix
[   41.114488] ata3: SATA max UDMA/133 cmd 0xe080 ctl 0xe000 bmdma 0xd800 irq 19
[   41.114491] ata4: SATA max UDMA/133 cmd 0xdc00 ctl 0xd880 bmdma 0xd808 irq 19
[   41.201116] usb 1-2: device not accepting address 2, error -71
[   41.461095] Driver 'sd' needs updating - please use bus_type methods
[   41.461166] sd 0:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
[   41.461176] sd 0:0:0:0: [sda] Write Protect is off
[   41.461178] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   41.461191] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   41.461232] sd 0:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
[   41.461241] sd 0:0:0:0: [sda] Write Protect is off
[   41.461242] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   41.461256] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   41.461258]  sda: sda1 sda2 sda3
[   41.503715] sd 0:0:0:0: [sda] Attached SCSI disk
[   41.507703] sd 0:0:0:0: Attached scsi generic sg0 type 0

```

Thanks in advance for the help.

---

