---
title: "Help with slow disk performance"
date: 2008-04-27
forum: General Help
---

### Post by Jungleboss on 2008-04-27
In Gutsy I used ext3 with writeback enabled for my partitions but suffered from bad disk performance (especially multitasking disk performance, but also rather slow sequential read/write performance).

Now in Hardy I thought i'd try some other file systems and now my work disk is using xfs and my boot partition reiser fs.

However I still have major problems (even more than before!)

Examples: Par2 verify a 4.4 gb file took 25 min! And unraring it took 6 min.

I'm using AHCI through the Intel ICH8 chipset.
Performance is much better in Windows XP.

I have no ideas how to fix this..

This is the config for the partitions in my fstab.
[FONT="Courier New"]
# /dev/sdb1
UUID=63c69e4c-1026-4633-89f8-78ac7b696bbb /               reiserfs notail,relatime 0       1

# /dev/sdb2
UUID=2d791175-dc45-4dd2-81fd-f34fdb620690 /media/sdb2     xfs     relatime        0       2[/FONT]

And according to hdparm dma should be enabled:

[FONT="Courier New"]sudo hdparm -I /dev/sdb

/dev/sdb:

ATA device, with non-removable media
	Model Number:       ST3400620AS                             
	Serial Number:      5QG0S9HA
	Firmware Revision:  3.AAC   
Standards:
	Supported: 7 6 5 4 
	Likely used: 7
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  781422768
	device size with M = 1024*1024:      381554 MBytes
	device size with M = 1000*1000:      400088 MBytes (400 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Recommended acoustic management value: 254, current value: 0
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	DOWNLOAD_MICROCODE
	    	SET_MAX security extension
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	SATA-II signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Phy event counters
	    	Device-initiated interface power management
	   *	Software settings preservation
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
	not	supported: enhanced erase
Checksum: correct[/FONT]

---

