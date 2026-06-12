---
title: "Slow file copying to HDD and external devices"
date: 2008-06-20
forum: General Help
---

### Post by Arlanthir on 2008-06-20
I had a previous thread about this here: [old thread]("http://ubuntuforums.org/showthread.php?t=827508")

Basically I'm experiencing slow copying of large files since a while ago, and I've seen more people with the same problems.

The symptoms are easily noticed: Copy a large file, preferably from your HDD to an external device and watch the percentage. If you have this problem, it will take more and more time with each 1%, with the copying getting slower each time. At first nautilus will say "28 seconds remaining" but once you get to 1/3 of the file you will have "2 minutes remaining" and then it just keeps climbing up as the bar SLOWLY progresses. Eventually the copy will end, but taking a lot more of time than predicted. This only affects Linux.



Some outputs for (probably) useful stuff:

sudo hdparm -cudagiI /dev/sda
```
/dev/sda:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 readahead     = 256 (on)
 geometry      = 9729/255/63, sectors = 156301488, start = 0

 Model=ST98823AS                               , FwRev=3.05    , SerialNo=            3PK0K780
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode


ATA device, with non-removable media
	Model Number:       ST98823AS                               
	Serial Number:      3PK0K780
	Firmware Revision:  3.05    
Standards:
	Supported: 7 6 5 4 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  156301488
	LBA48  user addressable sectors:  156301488
	device size with M = 1024*1024:       76319 MBytes
	device size with M = 1000*1000:       80026 MBytes (80 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: 128
	Recommended acoustic management value: 254, current value: 0
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	DOWNLOAD_MICROCODE
	   *	Advanced Power Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	IDLE_IMMEDIATE with UNLOAD
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	Phy event counters
	    	Device-initiated interface power management
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
Checksum: correct
```


sudo hdparm -Tt /dev/sda
```
/dev/sda:
 Timing cached reads:   2228 MB in  2.00 seconds = 1114.28 MB/sec
 Timing buffered disk reads:   50 MB in  3.05 seconds =  16.40 MB/sec
```

**Note:** After some of the updates I ran (I keep my machine always up-to-date) it improved: from 16.40 to 35.25!
I still have the other problems, though.


lsmod | grep ata
```
ata_generic             8324  0 
pata_acpi               8320  0 
ata_piix               19588  1 
libata                159344  4 ata_generic,pata_acpi,ahci,ata_piix
scsi_mod              151436  6 sbp2,sg,sr_mod,sd_mod,usb_storage,libata
```


dmesg | grep ata
```
[    0.000000] ACPI: SSDT 3FE8C1AC, 020A (r1 SataRe SataAhci     1000 INTL 20060217)
[   10.324464] Memory: 1025904k/1047040k available (2177k kernel code, 20492k reserved, 1006k data, 368k init, 129536k highmem)
[   10.324490]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   11.352838] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[   23.441883] libata version 3.00 loaded.
[   23.877398] ata_piix 0000:00:1f.1: version 2.12
[   23.877661] scsi0 : ata_piix
[   23.878646] scsi1 : ata_piix
[   23.879411] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[   23.879417] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[   24.197093] ata1.00: ATAPI: HL-DT-ST DVDRAM GMA-4082N, HQ04, max MWDMA2
[   24.368767] ata1.00: configured for MWDMA2
[   24.368859] ata2: port disabled. ignoring.
[   24.806930] ata3: SATA max UDMA/133 abar m1024@0xd2404400 port 0xd2404500 irq 219
[   24.806936] ata4: SATA max UDMA/133 abar m1024@0xd2404400 port 0xd2404580 irq 219
[   24.806942] ata5: SATA max UDMA/133 abar m1024@0xd2404400 port 0xd2404600 irq 219
[   24.806948] ata6: SATA max UDMA/133 abar m1024@0xd2404400 port 0xd2404680 irq 219
[   24.975201] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   24.976208] ata3.00: ATA-7: ST98823AS, 3.05, max UDMA/100
[   24.976214] ata3.00: 156301488 sectors, multi 16: LBA48 
[   24.979933] ata3.00: configured for UDMA/100
[   25.044458] ata4: SATA link down (SStatus 0 SControl 0)
[   25.109897] ata5: SATA link down (SStatus 0 SControl 0)
[   25.175686] ata6: SATA link down (SStatus 0 SControl 0)
[   26.082857] EXT3-fs: mounted filesystem with ordered data mode.
```


cat /etc/modules
```
fuse
lp
sbp2

```



sudo lshw -C cpu
```
*-cpu:0                 
       description: CPU
       product: Genuine Intel(R) CPU           T2400  @ 1.83GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 6.14.8
       serial: 0000-06E8-0000-0000-0000-0000
       slot: U1
       size: 1833MHz
       capacity: 1833MHz
       width: 32 bits
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor vmx est tm2 xtpr cpufreq
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          width: 32 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          width: 32 bits
          capabilities: logical
  *-cpu:1
       physical id: 1
       bus info: cpu@1
       version: 6.14.8
       serial: 0000-06E8-0000-0000-0000-0000
       size: 1833MHz
       capacity: 1833MHz
       capabilities: vmx ht cpufreq
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          capabilities: logical
```


sudo lshw -C disk
```
 *-cdrom                 
       description: DVD-RAM writer
       product: DVDRAM GMA-4082N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: HQ04
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
  *-disk
       description: ATA Disk
       product: ST98823AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.05
       serial: 3PK0K780
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=b308b308
  *-disk
       description: SCSI Disk
       product: 3200BEV External
       vendor: WD
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: 1.04
       serial: WD-WXE108L03694
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4 signature=5b6ac646
```


lsmod | grep ide
```

video                  19856  5 
output                  4736  1 video
arlanthir@Icarus:~$ uname -r
2.6.24-19-generic
```


hdparm -d1 /dev/sda
```
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
```


I'm sorry for the lengthy post, but it goes to show how much info unutbu required me to see if we could fix this. =/

---

### Post by Arlanthir on 2008-06-23
Just bumping and wishing someone who can help reads this..

---

### Post by unutbu on 2008-06-23
Would you post
```

dmesg > dmesg.log
sudo lspci -vvnn > lspci-vvnn.log
```

---

### Post by Arlanthir on 2008-06-23
Of course, here you go... You're the only one that has a clue about this, it seems! 

I had to upload them in .zip because the limit for txts is very low.

---

### Post by unutbu on 2008-06-23
After reading [http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html](http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html)
I realized that you are currently running with (E)IDE 32-bit I/O support disabled:

```

sudo hdparm -cudagiI /dev/sda
/dev/sda:
** IO_support    =  0 (default) **
```

If you type "man hdparm" you will find
```

       -c     Query/enable (E)IDE 32-bit I/O support.  A numeric parameter can be  used
              to  enable/disable 32-bit I/O support: Currently supported values include
              0 to disable 32-bit I/O support, 1 to enable 32-bit data transfers, and [B]3
              to  enable 32-bit data transfers with a special sync sequence required by
              many chipsets.  The value 3 works with nearly all  32-bit  IDE  chipsets,
              but  incurs  slightly  more  overhead.[/B]
```

I read somewhere that -c3 is safer than -c1. So perhaps try:

```
sudo hdparm -c3 /dev/sda
```

Then try 
```

sudo hdparm -Tt /dev/sda 
```
to see if there is any improvement.

Would you also run the test.pl script and post cptimes.dat again?

---

### Post by SabreWolfy on 2008-06-24
I'm just looking at this myself at the moment:

**60GB 4200rpm ATA drive in laptop:**
Timing cached reads:   950 MB in  2.00 seconds = 474.86 MB/sec
Timing buffered disk reads:   84 MB in  3.07 seconds =  27.39 MB/sec

**160GB [COLOR="Red"]7200[/COLOR]rpm ATA drive in desktop:**
Timing cached reads:   172 MB in  2.01 seconds =  85.53 MB/sec
Timing buffered disk reads:   58 MB in  3.05 seconds =  18.99 MB/sec

Neither of them accept the "-c3" parameter mentioned previously.

Any suggestions?

*Edit: The internal drive mentioned above and an external USB on the laptop both return high values. However, the drive in the desktop (mentioned above) AND the second drive in that machine BOTH return the very slow speeds. Could this be related to a BIOS setting? I have both drives set to auto-detect in the BIOS. I've changed the drive mode (large, lba, normal) but this did not seem to make any difference -- I've left it on auto-detect now too. This certainly explains why the performance of my new 160GB drive has been so bad! None of the drives will accept the "-c3" parameter [COLOR="Blue"][setting 32-bit IO_support flag to 3 // HDIO_SET_32BIT failed: Invalid argument][/COLOR]. Also, the BIOS reports that the drive is 136GB when it auto-detects it from within the BIOS menus. Ubuntu reports it as 160GB, as does the manufacturer's bootable CD ROM to test the drive. Would the poor performance in the desktop machine have anything to do with the fact that both drives are sharing the same IDE cable -- one is the master and the other the slave, on the same physical cable going to one connector on the motherboard? **Sigh** I really don't feel like opening up the box to check this ...*

[COLOR="DarkOrchid"]Edit: Disconnected the power and data cables from the second hard drive in the desktop machine and ran the tests again: No change. The 160GB 7200rpm drive still returns those dreadfully low values. _The 4200rpm in the laptop is more than 6 times faster!_[/COLOR]

---

### Post by unutbu on 2008-06-24
SabreWolfy, as I told Arlanthir, I am not an expert at fixing hard drive problems. I'm just an interested user trying to help.

It appears I was mistaken in my previous post. Although I believe my drive is behaving normally, I too have IO_support set to off:

```
% sudo hdparm -c /dev/sda

/dev/sda:
 IO_support    =  0 (default 16-bit)
```

and I can't seem to turn it on with hdparm:
```
% sudo hdparm -c3 /dev/sda

/dev/sda:
 setting 32-bit IO_support flag to 3
 HDIO_SET_32BIT failed: Invalid argument
 IO_support    =  0 (default 16-bit)

```
Like Arlanthir and probably you too SabreWolfy, I am using the libata driver, which seems to be the default HD driver but which does not have support for the full set of HDIO_* commands.

---

### Post by unutbu on 2008-06-24
SabreWolfy, would you please post (for both your laptop and desktop)

```
dmesg | grep -i ata
```

This will show what Linux thinks is the maximum transfer mode for your hard drives is, and also what actual transfer mode is being used. If DMA is not yet enabled, we may be able to increase your performance dramatically.

Also, I'm interested in collecting statistics about people's actual disk copy speeds. These appear to be much slower than the theoretical speeds achievable at each transfer mode. I'm still trying to figure out why and what needs to be done to increase actual speeds.

If you have have 4GB of free disk space on your laptop and/or your desktop, would you please run the benchmarking script posted here:
[http://ubuntuforums.org/showpost.php?p=5180093&postcount=6](http://ubuntuforums.org/showpost.php?p=5180093&postcount=6)
The 4GB is used to copy large files full of zeros. After the script is done timing the results, the large files full of zeros are deleted.

---

### Post by SabreWolfy on 2008-06-24
Yeah, I'm using *libata*, although with different parameters/values for the two machines (from *lsmod | grep ata*), which is understandable as they are quite different hardware and the desktop is quite old. How do we load another / better ATA driver?

Seems like such a waste to have a new 7200rpm drive which is not performing. There must be a way to solve this.

---

### Post by SabreWolfy on 2008-06-24
**Laptop:**

[    0.000000]  BIOS-e820: 000000004f680000 - 000000004f689000 (ACPI data)
[   11.690261] Memory: 1277256k/1300992k available (2177k kernel code, 22428k reserved, 1006k data, 368k init, 383488k highmem)
[   11.690277]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   12.356496] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[   15.712703] libata version 3.00 loaded.
[   16.171312] ata_piix 0000:00:1f.1: version 2.12
[   16.172064] scsi0 : ata_piix
[   16.172537] scsi1 : ata_piix
[   16.172809] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   16.172813] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   16.401022] ata1.00: ATA-6: IC25N060ATMR04-0, MO3OAD4A, max UDMA/100
[   16.401025] ata1.00: 117210240 sectors, multi 16: LBA48 
[   16.401051] ata1.01: ATAPI: QSI CD-RW/DVD-ROM SBW242C, UQ81, max UDMA/33
[   16.402183] ata1.00: configured for UDMA/100
[   16.408087] ata1.01: configured for UDMA/33
[   16.408580] ata2: port disabled. ignoring.
[   16.408718] scsi 0:0:0:0: Direct-Access     ATA      IC25N060ATMR04-0 MO3O PQ: 0 ANSI: 5
[   16.707160] EXT3-fs: mounted filesystem with ordered data mode.
[   22.383804] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   26.440117] EXT3-fs: mounted filesystem with ordered data mode.
[   27.471898] ACPI: \_SB_.PCI0.PATA.PRID.BAY_: found ejectable bay
[   27.471904] ACPI: \_SB_.PCI0.PATA.PRID.BAY_: Adding notify handler
[   27.471941] ACPI: Bay [\_SB_.PCI0.PATA.PRID.BAY_] Added
[   28.773748] ata2: port disabled. ignoring.
[   28.838157] ata1.01: ACPI cmd ef/03:0c:00:00:00:b0 filtered out
[   28.838160] ata1.01: ACPI cmd ef/03:41:00:00:00:b0 filtered out
[   28.838849] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[   28.838852] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[   28.839965] ata1.00: configured for UDMA/100
[   28.842125] ata1.01: configured for UDMA/33
[   29.617808] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   29.670986] ata2: port disabled. ignoring.
[   29.735223] ata1.01: ACPI cmd ef/03:0c:00:00:00:b0 filtered out
[   29.735226] ata1.01: ACPI cmd ef/03:41:00:00:00:b0 filtered out
[   29.735914] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[   29.735916] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[   29.737034] ata1.00: configured for UDMA/100
[   29.742003] ata1.01: configured for UDMA/33
[   30.424553] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   28.902428] ata2: port disabled. ignoring.
[   28.966172] ata1.01: ACPI cmd ef/03:0c:00:00:00:b0 filtered out
[   28.966175] ata1.01: ACPI cmd ef/03:41:00:00:00:b0 filtered out
[   28.966862] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[   28.966865] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[   28.967980] ata1.00: configured for UDMA/100
[   28.970135] ata1.01: configured for UDMA/33
[   64.760903] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   28.910623] ata2: port disabled. ignoring.
[   28.972554] ata1.01: ACPI cmd ef/03:0c:00:00:00:b0 filtered out
[   28.972557] ata1.01: ACPI cmd ef/03:41:00:00:00:b0 filtered out
[   28.973249] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[   28.973252] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[   28.974368] ata1.00: configured for UDMA/100
[   28.976515] ata1.01: configured for UDMA/33
[   29.221225] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   27.844487] ata2: port disabled. ignoring.
[   27.906445] ata1.01: ACPI cmd ef/03:0c:00:00:00:b0 filtered out
[   27.906448] ata1.01: ACPI cmd ef/03:41:00:00:00:b0 filtered out
[   27.907140] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[   27.907143] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[   27.908262] ata1.00: configured for UDMA/100
[   27.910416] ata1.01: configured for UDMA/33
[   28.602917] ieee80211: 802.11 data/management/control stack, git-1.1.13

--------------------

**Desktop:**

[    0.000000]  BIOS-e820: 0000000013ff3000 - 0000000014000000 (ACPI data)
[   38.926502] Memory: 312580k/327616k available (2177k kernel code, 14432k reserved, 1006k data, 368k init, 0k highmem)
[   38.926539]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   44.959385] libata version 3.00 loaded.
[   45.011660] pata_via 0000:00:07.1: version 0.3.3
[   45.072709] scsi0 : pata_via
[   45.121582] scsi1 : pata_via
[   45.121773] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xd000 irq 14
[   45.121780] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xd008 irq 15
[   45.306170] ata1.00: ATA-7: WDC WD1600AABB-00PUA0, 00.07H00, max UDMA/100
[   45.306187] ata1.00: 312581808 sectors, multi 0: LBA48 
[   45.306250] ata1.01: ATA-4: ST36531A, 3.41, max UDMA/33
[   45.306256] ata1.01: 12706470 sectors, multi 0: LBA 
[   45.312224] ata1.00: configured for UDMA/66
[   45.327439] ata1.01: configured for UDMA/33
[   45.647730] ata2.01: ATAPI: GCR-8523B, 1.00, max MWDMA2
[   45.819693] ata2.01: configured for MWDMA2
[   45.821560] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600AABB-0 00.0 PQ: 0 ANSI: 5
[   45.821864] scsi 0:0:1:0: Direct-Access     ATA      ST36531A         3.41 PQ: 0 ANSI: 5
[   48.766219] EXT3-fs: mounted filesystem with ordered data mode.
[   80.575605] EXT3-fs: mounted filesystem with ordered data mode.
[  510.490011] EXT3-fs: mounted filesystem with ordered data mode.

----------

Hope that all makes sense to you!

---

### Post by SabreWolfy on 2008-06-24
Is [this]("http://ubuntuforums.org/showthread.php?t=815622") of any use? I see there are several bug reports relating to these issues, but they are for earlier versions of the kernel. I'm running 2.6.24-19.33 Ubuntu Hardy on both of the machines. In fact, the desktop machine is the "cache" for my updates, so they are both running the same version of everything. Of course, the hardware is very different.

In desperation, I've also flash the BIOS on the desktop machine, which had no effect, other than to cause the machine to spend ages and ages checking RAM at boot time, and I can't find a way to turn it off. I flashed it back to the previous version, but it still spends ages checking RAM.

Both version of the flash auto-detect the 160GB drive as 136GB. Whether I select this setting, or leave it on boot-time auto-detect, Ubuntu happily reports that it is a 146G[i]B drive. Of course 160GB actually means 149.05GiB. Not sure where the missing 3GB went; reserved space is added to the used space I thought, rather than subtracted from the total size.

---

### Post by Arlanthir on 2008-06-24
The changes in your test are minimal, I had seen it before so I didn't post them... When the kernel/gvfs updates again I'll test it one more time ;)

I'm really starting to think this is one of those things that will eventually be fixed in some update...

---

### Post by SabreWolfy on 2008-06-24
I hope so. I'm just amazed that there is such a difference in performance between two machines, both running the same version of Hardy kernel. I only installed the 160GB drive a few days ago, and I've been wondering about the poor performance. Laptop drive has always worked well (that I can recall).

---

### Post by unutbu on 2008-06-24
> 
... the drive in the desktop (mentioned above) AND the second drive in
that machine BOTH return the very slow speeds.... Would the poor performance in the
desktop machine have anything to do with the fact that both drives are sharing the same
IDE cable -- one is the master and the other the slave, on the same physical cable going
to one connector on the motherboard?

That's a very good question to which I don't know the answer. I may very well have something to do with the slowdown you are experiencing. Have you set the dip switches on the second drive to make it a slave? You might have to read the manual to find out what the right dip switch configuration is.

[http://en.kioskea.net/pc/ide-ata.php3](http://en.kioskea.net/pc/ide-ata.php3) has some information about the correct position the master and slave must be plugged into the ribbon cable.

There seem to be a number of issues involved:
1) The correct physical connection of the drives on the ribbon cable,
2) The dip switches on both drive, to set master and slave modes
3) The BIOS settings
4) The linux drivers
5) Whether or not both your drives are SATA, PATA or PATA+SATA

I have yet to wrap my mind around all these issues. I'll post if I find anything that might help you.

> Also, the BIOS reports that the drive is 136GB
when it auto-detects it from within the BIOS menus. 
 
[http://www.pcguide.com/ref/hdd/bios/size.htm](http://www.pcguide.com/ref/hdd/bios/size.htm) page has an explanation of why (I think) your BIOS is reporting the drive to be 136GB. I don't think this affects speed. It only becomes an issue when the BIOS has to boot an OS whose boot sectors lie beyond the 137GB limit.
That's not your problem at the moment.

---

### Post by unutbu on 2008-06-24
I think maybe SabreWolfy has found the solution in that link in post #11.
If you follow the children links, you find three instances of similar solutions:

[http://ubuntuforums.org/showpost.php?p=4218596&postcount=9](http://ubuntuforums.org/showpost.php?p=4218596&postcount=9)
[http://ubuntuforums.org/showpost.php?p=4218717&postcount=2](http://ubuntuforums.org/showpost.php?p=4218717&postcount=2)
[http://ubuntuforums.org/showpost.php?p=5096657&postcount=2](http://ubuntuforums.org/showpost.php?p=5096657&postcount=2)

For you Arlanthir, I think it means you want to edit /etc/initramfs-tools/modules
to include
```

ata_piix
blacklist ata_generic
blacklist pata_acpi
blacklist ahci
```

I chose these modules to blacklist because your lsmod shows

```
lsmod | grep ata
libata                159344  4 ata_generic,pata_acpi,ahci,ata_piix
```

ata_generic is the common module that all 3 solutions blacklist. The other two I'm suggesting to blacklist, because I think you only need ata_piix. Blacklisting will not prevent those extra modules from being loaded, it will (hopefully) only alter the order in which the modules get loaded. 

Then run 

```
sudo update-initramfs -u
```
to update the initramfs file. Then cross your fingers and reboot.

satreth warns in [http://ubuntuforums.org/showpost.php?p=4218717&postcount=2](http://ubuntuforums.org/showpost.php?p=4218717&postcount=2) that blacklisting the wrong modules can make your system unbootable. I'm still doing research on what to do in this case. I'm just so excited I wanted to share this with you first. Hope my excitement is not misplaced...

---

### Post by unutbu on 2008-06-24
/usr/sbin/update-initramfs is a script which alters /boot/initrd.img-*. So if the instructions above cause your computer to be unable to boot, then the fix is to boot from a LiveCD, then open a terminal:

```
sudo mkdir /Ubuntu
sudo mount /dev/sda1 /Ubuntu
```
(Change sda1 to the correct name for your linux partition).

```
sudo chroot /Ubuntu
gksudo gedit /etc/initramfs-tools/modules
```

Comment out or remove the changes. Save and exit gedit. Then

```
sudo update-initramfs -u
```

This will return initrd.img-* back to its prior state. Then you should be able to boot again.

---

### Post by Arlanthir on 2008-06-25
I definitely want to try that!
I'll post the results here in a while ;)

My modules list was empty, I just added your lines. Rebooting now (I can't actually cross my fingers because I'm typing, I hope it still works *grin*)


EDIT: No change :( It checked the disk at boot, other than that, everything's the same.

---

### Post by SabreWolfy on 2008-06-25
I tried the suggested blacklisting process too, but it made no difference. ata_piix is not listed in "lsmod | grep ata" on my desktop, but I added it to the modules list, added the blacklisting, ran the script and rebooted. System worked fine, but hard drive speed was still as slow as before.

These kinds of frustrations are what really disappoint me about Linux generally. I'm using Ubuntu and it is great, but something as fundamental as this is really important! I was previously trying to install Win9x into Virtual Box and it was taking SO LONG. Now I know why! During that process, before I knew about the hard drive speed tests, I booted into Win9x and tried installing Win9x that way. The installation FLEW! It took about three hours to go through the installation in Ubutnu via Virtual Box and it took about 30 minutes doing it natively in Win9x. How come Win9x can talk to my drive at top speed and the mighty Ubuntu Hardy Heron 8.04 LTS with all the latest patches and updates can't! Grrrr, this is *really* bugging me.

---

### Post by Arlanthir on 2008-06-25
That's not what saddens me, all software is susceptible to bugs. This is a hard one for me/you, but it's "just a bug" and Ubuntu is entitled to have them.

The problem for me is the fact that's a new bug, something all the other versions of Ubuntu did not have a problem with... It's some kind of stupid regression!

---

### Post by SabreWolfy on 2008-06-25
Booting off the Hardy Heron LiveCD: hard drive speed still slow.

Booting off PartedMagic LiveCD: hard drive speed still slow.

Booting off Damn Small Linux (kernel 2.4.x): hard drive speed faster! From about 80 to 185 for the first value.

---

### Post by unutbu on 2008-06-25
Arlanthir, sorry it didn't work. :( Back to the drawing board...

SabreWolfy, while using Damn Small Linux,
would you post the output of 

```
dmesg | grep -i ata
```

---

### Post by Arlanthir on 2008-06-25
Since you're in a testing spree, give it a go with Gutsy or another old version of Ubuntu. I have a feeling I never had this disk problems before!

And unutbu had a good idea, check the modules that are loaded and such.

I think it would be useful to post:

```

lsmod 
cat /etc/modules
cat /etc/initramfs-tools/modules

```

with Hardy and another version of Ubuntu (preferably) that works well.

---

### Post by SabreWolfy on 2008-06-25
> **unutbu said:**
> Arlanthir, sorry it didn't work. :( Back to the drawing board...

SabreWolfy, while using Damn Small Linux,
would you post the output of 

```
dmesg | grep -i ata
```

Right, after first working out how to mount USB drives in Damn Small Linux (/dev/sda1, despite hard drive being /dev/hda1) to copy the output, here it is:

```
<4> BIOS-e820: 0000000013ff3000 - 0000000014000000 (ACPI data)
<6>Memory: 320464k/327616k available (1386k kernel code, 6764k reserved, 567k data, 144k init, 0k highmem)
<4>hda: WDC WD1600AABB-00PUA0, ATA DISK drive
<4>hdb: ST36531A, ATA DISK drive
<4>hdc: ATAPI CDROM, ATAPI CD/DVD-ROM drive
<6>scsi0 : SCSI host adapter emulation for IDE ATAPI devices
<4>  Vendor:           Model: ATAPI CDROM       Rev: 140M
<6>Databook TCIC-2 PCMCIA probe: not found.
<7>WARNING: USB Mass Storage data integrity not assured
<6>EXT3-fs: mounted filesystem with ordered data mode.
<6>EXT3-fs: mounted filesystem with ordered data mode.
```

lsmod | grep -i ata returned nothing.

Strangely, my 160GB ext3 drive become corrupted at some point during my testing. I've managed to run a check on it and it's now ext2 and most of the data is still there. I wonder how it became corrupted? I'm not blaming Damn Small Linux or PartedMagic (I've used them several times before), but it certainly is strange. The drive is new and I have no reason to suspect there is anything wrong with it -- it has worked without fault (if slowly) during several attempted installations of Win9x, etc.

I've also solved the slow RAM checking I mentioned previously. I selected "Load Performance Defaults" which sped up the checking. I've no idea which actual setting it changed (maybe one not available otherwise).

---

### Post by SabreWolfy on 2008-06-25
> **Arlanthir said:**
> Since you're in a testing spree, give it a go with Gutsy or another old version of Ubuntu. I have a feeling I never had this disk problems before!

<snip>



The only other Live CD I have is Ubuntu 7.04 Beta. Booted from that. Hard drive speed is slow again (92 and 13 MB/sec).

What other factors are affecting this? I have fast hard drive access using Hardy on my laptop and on a desktop in my office. It's only the two drives in my "old" desktop at home which are slow. I've shown that the drives are fast in Damn Small Linux (186 and 9 MB/sec) [strange that the second value was lower] and that they (appear) to run very fast under native Win9x.

---

### Post by unutbu on 2008-06-25
This article [http://lwn.net/Articles/198344/](http://lwn.net/Articles/198344/) casts your problem in a historical perspective. It appears that PATA drives used to use a different driver which worked for older drives but was driving its maintainers insane -- they stopped developing support for new drives. So a new driver was written from the ground up. The result being libata plus its submodules
in /lib/modules/`uname -r`/kernel/drivers/ata.

Unfortunately, I think you are both getting bitten by this so-called improvement. It seems to me the current default Hardy system is not correctly enabling the full capability of your drives. 

One possibility which may lead to a solution is to find out more about which driver Damn Small Linux uses to control pata drives, and see if we can coax Hardy into using the same driver. 

Toward this end, SabreWolfy, would you run and post
```
dmesg > dmesg.out
sudo lspci -vvnn > lspci-vvnn.log
lsmod > lsmod.out
``` while running Damn Small Linux?

The previous dmesg command did not capture the info I wanted (my mistake).

Another avenue of attack is to file bug reports. Maybe that will bring this problem to the attention of people with more knowledge than me.
See [http://wiki.ubuntu.com/KernelTeamBugPolicies](http://wiki.ubuntu.com/KernelTeamBugPolicies) for some guidelines on filing good bug reports.

---

### Post by SabreWolfy on 2008-06-25
Thanks. I'll boot into Damn Small Linux again as soon as I can. I'm running an extended test on the drive now from a Western Digital boot CD.

Some links relating to this [here]("https://bugs.launchpad.net/ubuntu/+bug/216878") and [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94981"). The second one mentions that that specific issue is resolved.

---

### Post by Arlanthir on 2008-06-25
I downloaded Gutsy Gibbon again and tried to copy a large file with it.
Absolutely perfect, you can't even compare, and with a livecd..

So, here's the data I got, anything more you want, just ask and I'll repeat.

unutbu, you're helping a lot, at least keeping a focused point of research and trying fixes, it's not your fault that one doesn't work. I can't thank you enough! I'd thank you just for your effort with the board's system, but I'm holding on to that fix you're gonna find :D

---

### Post by SabreWolfy on 2008-06-26
And the "hdparm -Tt" results under Gutsy? Also better? That's very interesting, because I tried the 7.04 (Fiesty) Beta Live CD as I mentioned earlier and the "hdparm -Tt" tests was still slow. So it was fixed in Gutsy and then broken again in Hardy! :)

---

### Post by Arlanthir on 2008-06-26
My *hdparm -Tt* is not very bad, I guess, but it's equal both in Gutsy and in Hardy. That's not the problem. The problem is I transferred almost 2GB in 4 minutes with gutsy. With hardy, when I reach 4 minutes it's still saying that it will take more 13 minutes, and that time CLIMBS!

I think Feisty was good too, and the early versions of hardy could possibly be also. Today I will try the Hardy LiveCD and check it out. In my opinion, it was some update that broke it OR something I installed because I don't remember messing with anything this serious.

**EDIT:** I was wrong, Hardy LiveCD had the problem, just not so advanced! It took me 11 minutes to copy the same files Gutsy copies in 4. It started copying at 14.3mb/s but when it ended the average was down to 3.4mb/s. That's not bad, considering my test in Hardy installed and updated: started with 14.3mb/s too but in 10 minutes it was near 50% and the average speed was only 1.4mb/s!

---

### Post by SabreWolfy on 2008-06-26
> **unutbu said:**
> <snip>

Toward this end, SabreWolfy, would you run and post
```
dmesg > dmesg.out
sudo lspci -vvnn > lspci-vvnn.log
lsmod > lsmod.out
``` while running Damn Small Linux?

The previous dmesg command did not capture the info I wanted (my mistake).


Attached.

---

### Post by SabreWolfy on 2008-06-26
FWIW, I've booted of the OpenSuse 11 LiveCD and the Fedora9 LiveCD and run "hdparm -Tt". Both are returning the "slow" values. So far, only DSL is returning the "fast" values, which are a little over twice the slow values. However, in DSL the buffered read value is much *lower*, but this may be a result of the kind of installation it is? A really tiny one. The "slow" values I refer to are for the cached results: around 80MB/sec in Fiesty Beta Live CD, Hardy Live CD, Hardy install, OpenSuse LiveCD and Fedora LiveCD. DSL LiveCD returns a value of about 180MB/sec for the cached value. I haven't [yet] run the benchmark-hd.pl script on the 160GB desktop drive.

---

### Post by SabreWolfy on 2008-06-26
The 160GB drive in the desktop machine which used to house Hardy was corrupted at some point during my testing, so I decided to do a little more testing before reinstalling again properly. 

The only Gutsy image I have is the Xubuntu Alternate CD, so I installed this [as a command-line only installation, just to see how it works]. This installation uses */dev/hda1*, whereas Hardy uses */dev/sda1* I think. The "hdparm -Tt" command gave values of 92MB/sec and 20MB/sec, which are still "slow" values. Arlanthir mentioned in a previous post that performance was much faster in Gutsy than Hardy, although the hdparm values were approximately the same. I'll run the benchmark-hd script now in Gutsy and then install Hardy to compare.

[COLOR="Red"]When you run the *benchmark-hd.pl* script, make sure that you know whether your hard drives are *hda* or *sda*! I've just run the script now, with a flash disk plugged in to store the output, and the script tests *SDA*. As I mentioned above, in Xubuntu Gutsy command-line install (at least), the hard drive is *HDA*! So, I just ran the benchmark test on my flash disk. Not sure how this is possible, as it is a tiny 32MB flash disk, mounted into /home/"user".

Correct me if I'm wrong -- the file copying process takes place in the directory in which the script is run from, but the "hdparm" part of the script uses */dev/sda*. This may explain why Arlanthir is getting strange results ... ?[/COLOR]

---

### Post by SabreWolfy on 2008-06-26
Ok, here are the results of some testing. I ran the *benchmark-hd.pl* script (modified to refer to the hard drive in each case) in Xubuntu Gutsy command-line install and then in Hardy Live CD. I captured output from "lsmod", "lspci" and "dmesg", but I have not included it here, as I don't think there is anything new there.

**Gutsy:**
```
Benchmarking /dev/hda
1	1.02
2	0.12
4	0.56
8	0.64
16	1.71
32	2.93
64	7.41
128	13.56
256	26.89
512	53.80
1024	108.44

/dev/hda:
 Timing cached reads:   186 MB in  2.00 seconds =  92.88 MB/sec
 Timing buffered disk reads:   60 MB in  3.06 seconds =  19.61 MB/sec
```

**Hardy:**
```
Benchmarking /dev/sda
1	3.60
2	0.16
4	0.22
8	0.43
16	1.79
32	3.23
64	6.65
128	14.29
256	26.79
512	56.58
1024	111.77

/dev/sda:
 Timing cached reads:   172 MB in  2.00 seconds =  85.79 MB/sec
 Timing buffered disk reads:   60 MB in  3.05 seconds =  19.64 MB/sec
```

Not much difference between them. Hardy was running from a LiveCD, Gutsy from an actual install on the drive being tested.

Unfortunately, the benchmarking script does not run under DSL. The "hdparm" results, for reference, were:

**DSL:**
```

/dev/hda:
 Timing buffer-cache reads:   356 MB in  2.01 seconds = 177.11 MB/sec
 Timing buffered disk reads:   18 MB in  3.32 seconds =   5.42 MB/sec
```

Arch Linux (2.6.24-ARCH) command-line [used to install from] gives slow "hdparm" results. I didn't bother with the benchmark tests.

Vector Linux (2.6.22) installed to 160GB drive gives slow "hdparm" results.

---

### Post by Arlanthir on 2008-06-26
Is that benchmark the one from unutbu?
I'm not using that anymore because I couldn't test it with the live cd (it just created empty files for lack of space)

I'm using actual file copies in the same conditions to benchmark it a little. I've posted the results in my previous posts, it's strange how they differ from yours in terms of working better or not. I'm guessing we don't have exactly the same problem, and hdparm seems to suggest that. =/

---

### Post by SabreWolfy on 2008-06-26
> **Arlanthir said:**
> Is that benchmark the one from unutbu?
Yes.

> **Arlanthir said:**
> I'm not using that anymore because I couldn't test it with the live cd (it just created empty files for lack of space)
I tested it from the Hardy Live CD by mounting my hard drive into */media* and then running the script.

> **Arlanthir said:**
> I'm using actual file copies in the same conditions to benchmark it a little. I've posted the results in my previous posts, it's strange how they differ from yours in terms of working better or not. I'm guessing we don't have exactly the same problem, and hdparm seems to suggest that.
How are you timing them? Are you relying on Nautilus?

---

### Post by Arlanthir on 2008-06-26
Yes I am.

---

### Post by SabreWolfy on 2008-06-26
> **Arlanthir said:**
> Yes I am.

How do we know that it is accurate? I'm thinking of how hugely inaccurate similar timings were in W*ndows. Although I presume you are actually timing the copy yourself with a stopwatch or something? Or just "guestimating"?

---

### Post by Arlanthir on 2008-06-26
I don't think I need great benchmarking abilities to feel the difference from 4 minutes to 20+, so I'm kinda using that. :S That's how bad things are for me...

---

### Post by SabreWolfy on 2008-06-26
Time to give up on this issue. I don't know what's happening any more! I just installed a really old version of Mandrake Linux -- Version 7.1 (Helium). It runs kernel 2.2.15-4mdkfb. The results from "hdparm" are slow again: 85MB/sec and 5 MB/sec. So only DSL can get that first value up to around 185MB/sec, which is REALLY slow for a 7200rpm drive, in comparison to the +-650MB/sec and 27MB/sec I get on my internal 4200rpm drive and my USB drive, both in my laptop. The slow hard drive performance is from drives in an older machine: it's a P3 1GHz with 320MB RAM.

Remind me how you are doing your tests Arlanthir? You just copy a large file from one place on the disk to another? Or are you reading from one disk and writing to a different disk? The amount of fragmentation and the location of the free space on the disk would have an effect, but not such a large one.

---

### Post by Arlanthir on 2008-06-26
I copy a large file from one USB device to another and count the minutes.
Couldn't be more simple, and yet so different in results :S
None of that should have an effect, one device keeps unchanged and the other just adds/deletes the file.

---

### Post by unutbu on 2008-06-28
Arlanthir, do you have an AHCI setting in your BIOS? If so, try enabling it if it isn't enabled already.

I see you have an AHCI controller. 
> 00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 01) (prog-if 01 [AHCI 1.0])

I'm getting this tip from [http://ubuntuforums.org/showpost.php?p=5278430&postcount=28](http://ubuntuforums.org/showpost.php?p=5278430&postcount=28).

---

### Post by SabreWolfy on 2008-06-28
Arlanthir, have you considered "bonnie++"? Install with aptitude. I've run it on the Gutsy desktop and Hardy laptop. Trying to figure out what the results mean now.

---

### Post by Arlanthir on 2008-06-28
> **unutbu said:**
> Arlanthir, do you have an AHCI setting in your BIOS? If so, try enabling it if it isn't enabled already.

I see you have an AHCI controller. 


I'm getting this tip from [http://ubuntuforums.org/showpost.php?p=5278430&postcount=28](http://ubuntuforums.org/showpost.php?p=5278430&postcount=28).

I have shown you my BIOS settings screen, I'm afraid what you see is what you get :S
No more options than those =/


> **SabreWolfy said:**
> Arlanthir, have you considered "bonnie++"? Install with aptitude. I've run it on the Gutsy desktop and Hardy laptop. Trying to figure out what the results mean now.

Running it... ;)

---

### Post by SabreWolfy on 2008-06-28
Re bonnie++ ... only the last line (comma separated values) seems to be of any real value. If you take that line (the one at the end of the output, starting with your machine name) and save it as a file, then you can make an HTML version in a nice table for viewing with:

```
bon_cvs2html < TheFile.txt > TheFile.html
```

---

### Post by Arlanthir on 2008-06-28
It's bon_csv2html, TAB-key helped me :P
Will upload (containing the + at the end..)

---

### Post by SabreWolfy on 2008-06-28
Here are my results: first one is for the laptop (fast hard drive access with "hdparm") and the second is for the desktop (slow access):

---

### Post by Arlanthir on 2008-06-28
Do both of them have problems or only the last one is slow copying files?

---

### Post by SabreWolfy on 2008-06-28
First one is Hardy laptop, which works fine -- "hdparm" gives good results.

Second one is Gutsy desktop (although I've installed several different distros on here as I've mentioned previously) and it has very slow "hdparm" results. It's also an older machine with less RAM, but the difference seems to large.

---

### Post by SabreWolfy on 2008-06-29
I've spent some more time reading and thinking about the hard drive performance issues I mentioned earlier. The "hdparm" program returns two values (from the *man* page):

> -T <snip> This displays the speed of reading directly from the Linux buffer cache without disk access. This measurement is essentially an indication of the throughput of the processor, cache, and memory of the system under test.

This was returning high values (650MB/s) on my laptop internal drive and on the USB drive connected to my laptop, but slow values (80MB/s) for the 7200rpm drive in my (old) desktop machine; values of 185MB/s were obtained using Damn Small Linux (2.4.x kernel).

The other value returned is:

> -t <snip> This displays the speed of reading through the buffer cache to the disk without any prior caching of data. This measurement is an indication of how fast the drive can sustain sequential data reads under Linux, without any filesystem overhead.

This was returning values of about 27MB/s on laptop internal drive and USB drive on laptop, and about 20MB/s on desktop; lower values were returned using Damn Small Linux.

I'm taking the second of these values (-t) as more representative of what the drive is actually doing. The first one (-T) seems to depend more on the other hardware in the machine. Why the installation of Windows in Virtual Box took 2+ hours compared to 30 minutes when booted into DOS I cannot explain. The manual for the motherboard in the desktop machine mentions that the IDE bus masters are DMA33/ATA66, which I think means 66MB/s maximum throughput. I suppose 20MB/s is quite slow then. All told, I'm not sure what -- if anything -- I can really do about this. I'm feel that disk access in Windows (booted natively) is much faster than through Ubuntu Hardy, but I have spent enough time on this problem. I'm considering the matter "closed" now, until I can find any new information.

---

### Post by SabreWolfy on 2008-06-29
> **Arlanthir said:**
> Do both of them have problems or only the last one is slow copying files?

Both drives in the old desktop machine return similar values from "hdparm". The one drive is a new 160GB 7200rpm and the other is an old slow 6.5GB 5400rpm. I would love to test one or both of them connected to my laptop, but I don't have a 3.5" IDE USB enclosure (and the cost of them here is about half the cost of the 160GB drive!)

---

### Post by Arlanthir on 2008-06-29
Don't know what to do also, but I'm not very literate in any of this. It doesn't annoy me too much, so I guess I'll be waiting for it to be fixed in some update, which will take less than 6 months (worst case scenario) :P

---

### Post by SabreWolfy on 2008-06-30
For what it's worth, I thought I'd try two more distributions:

The Gentoo LiveCD 2007.0, using kernel 2.6.19-gentoo-r5, gives FAST results from "hdparm" for both drives on the old desktop machine: 185MB/s cached and 10MB/s buffered.

Damn Small Linux Not, using kernel 2.6.12, gives FAST results (180MB/s) for cached reads and SLOW results (5MB/s) for buffered reads.

---

### Post by Arlanthir on 2008-06-30
My laptop went to HP repair, so, no more testing from me =/

---

### Post by unutbu on 2008-06-30
I don't think I can help you guys. Though experimenting with different distros may be a way to escape the problem. Other than that, I think this problem may require the help of developers (in the form of an update). 

To help me follow along with your experiments SabreWolfy, would you please fill in / correct this table:
```

desktop 7200rpm
                                            cached      buffered    1GB cp
Gentoo LiveCD 2007.0 (2.6.19-gentoo-r5)     185         10          ?
DSL                  (2.6.12)               177--185    5.42        ?
?                    (?)                    80          20
Gutsy Xubuntu Alt CD (?)                    92.88       19.61       108.44
Hardy                (?)                    85.79       19.64       111.77
Mandrake 7.1         (2.2.15-4mdkfb)        85          5


laptop internal (4200rpm)
                                            650         27
laptop USB       
                                            650

```

---

### Post by SabreWolfy on 2008-06-30
> **unutbu said:**
> To help me follow along with your experiments SabreWolfy, would you please fill in / correct this table:

Ah, that's a great idea! I'll do my best to fill in all the missing values, but it might take a while as I have less free time at the moment. I'll post here when I've done it all.

[COLOR="Blue"]Edit: I am no longer using the desktop machine and am not in a position to complete the table unfortunately. IIRC, the benchmarking script did not run in DSL, DSL-N and Gentoo. I have removed the 160GB drive, so if I use it in any other machine, I'll be sure to make a note of its performance.[/COLOR]

---

### Post by MountainX on 2008-08-06
> **SabreWolfy said:**
> Arlanthir, have you considered "bonnie++"? Install with aptitude. I've run it on the Gutsy desktop and Hardy laptop. Trying to figure out what the results mean now.


Anyone else seeing this error with bonnie++ ?
```
Can't open file ./Bonnie.15315.000

```

---

### Post by SabreWolfy on 2008-08-06
> **MountainX said:**
> Anyone else seeing this error with bonnie++ ?
```
Can't open file ./Bonnie.15315.000

```

Sorry, didn't come across it when I was using the program.

---

### Post by SabreWolfy on 2008-08-06
On the previous issue of slow HDD performance, see [here]("http://bugs.launchpad.net/ubuntu/+bug/155511"), [here]("http://bugs.launchpad.net/ubuntu/+bug/216878") and [here]("http://bugs.launchpad.net/ubuntu/+bug/238788").

---

### Post by MountainX on 2008-08-06
> **SabreWolfy said:**
> Sorry, didn't come across it when I was using the program.

when I ran bonnie++ from my /home folder, the error went away.

---

### Post by MountainX on 2008-08-06
> **SabreWolfy said:**
> On the previous issue of slow HDD performance, see [here]("http://bugs.launchpad.net/ubuntu/+bug/155511"), [here]("http://bugs.launchpad.net/ubuntu/+bug/216878") and [here]("http://bugs.launchpad.net/ubuntu/+bug/238788").

great links. thanks!

---

### Post by SabreWolfy on 2008-08-12
On my system, I think the poor HDD performance is related to the fact that drivers for my chipset (via82cxxx) are no longer included in Ubuntu I have discovered.

Launchpad Bug Report [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217511").

Possible fixes provided in Launchpad [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213639") for "older" kernel versions than the one I am running.

---

### Post by unutbu on 2008-08-16
I've written a script which can copy a directory from one location to another. It does this by tar'ing the directory, then splitting it into smaller pieces, moving each small piece one-by-one, re-assembling the small pieces into a tar file, and then untar'ing it.

If you are still experiencing the slow copying problem for large files, it might be interesting to see if this script can speed up the transfer.

Save this in a file called lcp :
```

#!/usr/bin/env python

from tempfile import mkdtemp
from os import makedirs,listdir
from os.path import join,isdir
from shutil import move
from subprocess import call
from optparse import OptionParser
from time import time

parser = OptionParser()
parser.add_option("-s", "--source", dest="source",
                  help="source directory", metavar="DIR")
parser.add_option("-t", "--target", dest="target",
                  help="target directory", metavar="DIR")
parser.add_option("-m", "--megabytes", dest="megabytes", default=1,
                  help="size of the smaller split files", metavar="MEGABYTES")
parser.add_option("-v", "--verbose",
                  action="store_true", dest="verbose", default=False,
                  help="print status messages to stdout")

(opt, args) = parser.parse_args()

def warn(msg):
    if opt.verbose:
        print msg

if not opt.source or not opt.target:
    parser.print_help()
    exit(1)


if not isdir(opt.source):
    warn("'%s' does not exist"%opt.source)
    exit(1)
if not isdir(opt.target):
    warn("making directory '%s'"%opt.target)
    makedirs(opt.target)
try:
    opt.megabytes=int(opt.megabytes)
except ValueError:
    warn("-m expects an integer")
    exit(1)

warn("source dir: %s"%opt.source)
warn("target dir: %s"%opt.target)

source_workdir=mkdtemp()
target_workdir=mkdtemp(dir=opt.target)

warn("source_workdir dir: %s"%source_workdir)
warn("target_workdir dir: %s"%target_workdir)

t1=time()

tarfile=join(source_workdir,'temp.tar')
warn("Creating tar file '%s'"%tarfile)
call(['tar','cf',tarfile,'.'],cwd=opt.source)

warn("Splitting tar file")
msize='%sm'%opt.megabytes
call(['split','--bytes',msize,tarfile],cwd=source_workdir)

warn("Removing tar file '%s'"%tarfile)
call(['rm',tarfile],cwd=source_workdir)

small_files=listdir(source_workdir)
small_files.sort()
warn("List of small files: %s"%small_files)

for filename in small_files:
    smallfile=join(source_workdir,filename)
    move(smallfile,target_workdir)
    warn("Moving %s to %s"%(smallfile,target_workdir))

target_tarfile=join(opt.target,'temp.tar')
sock=open(target_tarfile,'w')

warn("Reassembling small files into %s"%target_tarfile)
cmd=['cat']
cmd.extend(small_files)
call(cmd, cwd=target_workdir, stdout=sock)
sock.close()

warn("Removing small files")
cmd=['rm']
cmd.extend(small_files)
call(cmd,cwd=target_workdir)

warn("Extracting tar file '%s'"%target_tarfile)
call(['tar','-C',opt.target,'-xf',target_tarfile])

warn("Removing %s"%target_tarfile)
call(['rm',target_tarfile])

warn("Cleaning up working directories")
call(['rm','-rf',target_workdir])
call(['rm','-rf',source_workdir])

warn("A copy of %s is now at %s"%(opt.source,opt.target))

t2=time()
dt=t2-t1

print "%0.3f seconds elapsed"%dt

```
Make it executable:
```

chmod 755 lcp

```
Run it like this:
```

lcp -s test -t test-0 
```
This copies the test directory to test-0. 
When run with the verbose flag, the output looks like this:
```

% lcp -s test -t test-0 -v
making directory 'test-0'
source dir: test
target dir: test-0
source_workdir dir: /tmp/tmpVc_4x7
target_workdir dir: test-0/tmpmAEjXZ
Creating tar file '/tmp/tmpVc_4x7/temp.tar'
Splitting tar file
Removing tar file '/tmp/tmpVc_4x7/temp.tar'
List of small files: ['xaa', 'xab', 'xac', 'xad']
Moving /tmp/tmpVc_4x7/xaa to test-0/tmpmAEjXZ
Moving /tmp/tmpVc_4x7/xab to test-0/tmpmAEjXZ
Moving /tmp/tmpVc_4x7/xac to test-0/tmpmAEjXZ
Moving /tmp/tmpVc_4x7/xad to test-0/tmpmAEjXZ
Reassembling small files into test-0/temp.tar
Removing small files
Extracting tar file 'test-0/temp.tar'
Removing test-0/temp.tar
Cleaning up working directories
A copy of test is now at test-0
0.117 seconds elapsed

```
You can also control the size of the small files that split creates:
```

% lcp -s test -t test-0 -v -m 5
```

The above command splits the tar file into pieces each no bigger than 5MB in size.

```
% lcp
Usage: lcp [options]

Options:
  -h, --help            show this help message and exit
  -s DIR, --source=DIR  source directory
  -t DIR, --target=DIR  target directory
  -m MEGABYTES, --megabytes=MEGABYTES
                        size of the smaller split files
  -v, --verbose         print status messages to stdout

```

---

### Post by Hiperi0n on 2008-09-05
I have experienced the same problem, however, I solved it by adding the async option in the external hdd line in /etc/fstab

It should work

---

