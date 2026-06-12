---
title: "To Everyone Dealing With Slow Hard Drives"
date: 2007-05-26
forum: General Help
---

### Post by DBO on 2007-05-26
Ok I can't promise you an answer... but I think I have stumbled across a rather important clue to what is going on here.  There are a large number of users reporting slow hard drive access, read and write times are going through the floor and performance is suffering.  By pure luck I happen to have two identical hard drives, not in RAID, with different results.  One is experiencing the slowdown after feisty and the other is not.  So I started looking into the differences between the two.


Hard drive one output from hdparm -I
> 
/dev/sda:

ATA device, with non-removable media
	Model Number:       Maxtor 6B250S0                          
	Serial Number:      B62076CH            
	Firmware Revision:  BANC1G10
Standards:
	Used: ATA/ATAPI-7 T13 1532D revision 0 
	Supported: 7 6 5 4 
Configuration:
	Logical		max	current
	cylinders	16383	0
	heads		16	0
	sectors/track	63	0
	--
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  490234752
	device size with M = 1024*1024:      239372 MBytes
	device size with M = 1000*1000:      251000 MBytes (251 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: unknown setting (0x0000)
	Recommended acoustic management value: 192, current value: 254
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
	   *	WRITE_VERIFY command
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	    	Advanced Power Management feature set
	    	SET_MAX security extension
	   *	Automatic Acoustic Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	    	Media Card Pass-Through
	   *	General Purpose Logging feature set
	   *	WRITE_{DMA|MULTIPLE}_FUA_EXT
	   *	URG for READ_STREAM[_DMA]_EXT
	   *	URG for WRITE_STREAM[_DMA]_EXT
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	Native Command Queueing (NCQ)
	    	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Data Tables (AC5)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
	not	supported: enhanced erase
Checksum: correct

and hard drive 2:
> 
/dev/sdb:

ATA device, with non-removable media
	Model Number:       Maxtor 6B250S0                          
	Serial Number:      B5D2AZKH            
	Firmware Revision:  BANC1G10
Standards:
	Used: ATA/ATAPI-7 T13 1532D revision 0 
	Supported: 7 6 5 4 
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  490234752
	device size with M = 1024*1024:      239372 MBytes
	device size with M = 1000*1000:      251000 MBytes (251 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: unknown setting (0x0000)
	Recommended acoustic management value: 192, current value: 254
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
	   *	WRITE_VERIFY command
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	    	Advanced Power Management feature set
	    	SET_MAX security extension
	   *	Automatic Acoustic Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	    	Media Card Pass-Through
	   *	General Purpose Logging feature set
	   *	WRITE_{DMA|MULTIPLE}_FUA_EXT
	   *	URG for READ_STREAM[_DMA]_EXT
	   *	URG for WRITE_STREAM[_DMA]_EXT
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	Native Command Queueing (NCQ)
	    	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Data Tables (AC5)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
	not	supported: enhanced erase
Checksum: correct

If you don't see the difference, I didn't either till I did a diff.  The big differences is this line here in /dev/sdb output:
> CHS current addressable sectors:   16514064

This drive also shows up as being addressed CHS... which is an older tech, but oddly enough this is the drive that is not experiencing performance issues.  What does any of this mean?  I suspect there is some kind of regression in libata dealing with addressing schemes for the hard drives.  I hope the kernel team can take a look and see if this is the case.  If other users experiencing similar issues could paste their output here, it will help me make a case on launchpad and maybe we can get some attention from the kernel team.

For reference I was playing around moving 6 files totalling a 1024MB worth of data using the time command to get timings.

/dev/sdb: 28 seconds
/dev/sda: 1 minute 8 seconds

---

### Post by vtel57 on 2007-05-27
Learn about hdparm also. It could be very helpful in tweaking your drive performance.

[http://articles.techrepublic.com.com/5100-10877_11-5551745.html](http://articles.techrepublic.com.com/5100-10877_11-5551745.html)

Luck!

---

### Post by DBO on 2007-05-27
Its often useful to read a thread before posting =P

I cant use hdparm because I have SATA drives.

---

### Post by atlfalcons866 on 2007-05-27
is direct memory turned (DMA) turned on

---

### Post by vtel57 on 2007-05-27
Hmm... I'm kinda' glad I'm still running Dapper. :)

---

