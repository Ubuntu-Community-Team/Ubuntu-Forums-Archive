---
title: "Problem with Nero Linux"
date: 2007-07-11
forum: General Help
---

### Post by Znort_Ubern00b on 2007-07-11
Hey all,

Having trouble burning DVDs with Nero Linux. Got .iso file and when i try to burn it I get this error log.

> 

Linux 2.6.20-16-generic
Nero API version: 7.5.14.4
Using interface version: 7.5.0.2
Installed in: /usr/lib/nero/
Application: Nero AG\Nero Linux
Internal Version: 7, 5, 14, 4

Recorder:             <_NEC DVD_RW ND-2500A>    Version: 1.06 - HA 0 TA 0 - 0.0.0.0
 Adapter driver:      <ata_piix>                HA 0
 Drive buffer  :      2048kB
 Bus Type      :      default (0) -> SCSI, detected: ?
Excluded drive IDs: 
WriteBufferSize: 83886080 (0) Byte
BUFE           : 0
Physical memory     : 1010MB (1035072kB)
Free physical memory: 14MB (14848kB)
Memory in use       : 98 %
Uncached PFiles: 0x0
Use Inquiry    : 1
Global Bus Type: default (0)
Check supported media : Disabled (0) 

11.7.2007
NeroAPI
17:49:28	#1 Text 0 File Burncd.cpp, Line 3490
	Turn on Disc-At-Once, using DVD media
	
17:49:29	#2 Text 0 File DlgWaitCD.cpp, Line 307
	Last possible write address on media:  2298495 (510:46.45, 4489MB)
	Last address to be written:             359064 ( 79:47.39,  701MB)
	
17:49:29	#3 Text 0 File DlgWaitCD.cpp, Line 319
	Write in overburning mode: NO
	
17:49:29	#4 Text 0 File DlgWaitCD.cpp, Line 2951
	Recorder: _NEC DVD_RW ND-2500A, Media type: DVD-R
	 Disc Manufacturer: CMC MA - G. AM3
	 Disc Application Code: 64, Disc Physical Code: 193
	
17:49:29	#5 Text 0 File DlgWaitCD.cpp, Line 493
	>>> Protocol of DlgWaitCD activities: <<<
	=========================================
	
17:49:29	#6 Text 0 File ThreadedTransferInterface.cpp, Line 792
	Setup items (after recorder preparation)
	 0: TRM_DATA_MODE1 (2 - CD-ROM Mode 1, Joliet)
	    2 indices, index0 (150) not provided
	    original disc pos #0 + 359065 (359065) = #359065/79:47.40
	    not relocatable, disc pos for caching/writing not required/not required
	    -> TRM_DATA_MODE1, 2048, config 0, wanted index0 0 blocks, length 359065 blocks [_NEC DVD_RW ND-2500A (H:0 T:0)]
	--------------------------------------------------------------
	
17:49:29	#7 Text 0 File ThreadedTransferInterface.cpp, Line 995
	Prepare [_NEC DVD_RW ND-2500A (H:0 T:0)] for write in CUE-sheet-DAO
	DAO infos:
	==========
	 MCN: ""
	 TOCType: 0x00; Session Closed, disc fixated
	 Tracks 1 to 1:                                  Idx 0         Idx 1      Next Trk
	   1: TRM_DATA_MODE1, 2048/0x00, FilePos             0             0     735365120, ISRC ""
	DAO layout:
	===========
	 ___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
	        0 |  lead-in |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   1 |    0x41 |   359065 |   359065 | 0x00
	   359065 | lead-out |   1 |    0x41 |        0 |        0 | 0x00
	
17:49:29	#8 Text 0 File Burncd.cpp, Line 4263
	Caching options: cache CDRom or Network-No, small files-Yes (<32KB)
	
17:49:29	#9 Phase 24 File ExtendedProgress.cpp, Line 537
	Caching of files started
	
17:49:29	#10 Text 0 File Burncd.cpp, Line 4382
	Cache writing successful.
	
17:49:29	#11 Phase 25 File ExtendedProgress.cpp, Line 537
	Caching of files completed
	
17:49:29	#12 Phase 28 File ExtendedProgress.cpp, Line 537
	Speed measurement started
	
17:49:29	#13 Text 0 File ThreadedTransferInterface.cpp, Line 2712
	Verifying disc position of item 0 (not relocatable, no disc pos, no patch infos, orig at #0): write at #0
	
17:49:29	#14 Text 0 File ThreadedTransfer.cpp, Line 269
	Pipe memory size 590400
	
17:49:48	#15 Text 0 File WriterStatus.cpp, Line 113
	<_NEC DVD_RW ND-2500A (H:0 T:0)> start writing Lead-Out at LBA 359065 (57A99h), length 0 blocks
	
17:49:48	#16 Phase 29 File ExtendedProgress.cpp, Line 470
	Speed measurement completed: 27.9x (38566 KB/s)
	
17:49:48	#17 Phase 36 File ExtendedProgress.cpp, Line 537
	Burn process started at 8x (11080 KB/s)
	
17:49:48	#18 Text 0 File ThreadedTransferInterface.cpp, Line 2712
	Verifying disc position of item 0 (not relocatable, no disc pos, no patch infos, orig at #0): write at #0
	
17:49:48	#19 Text 0 File DVDR.cpp, Line 3153
	Recording mode: Sequential Recording Mode
	
17:49:48	#20 Text 0 File DVDR.cpp, Line 3309
	Start write address at LBA 0
	DVD high compatibility mode: Yes
	
17:49:48	#21 Text 0 File Cdrdrv.cpp, Line 9886
	---- Disc Structure: Physical Format Information (00h) ----
	Media Type: 0, Layer: 0, Address: 0 (0 h), AGID: 0; Length: 2050
	 Book Type: DVD-R (2), Part Version: 2.0x (5), Extended Part Version: 2.1 (33)
	 Disc Size: 120 mm,      Maximum Rate: <not specified> (F h)
	 Number of Layers: 1,    Track Path: Parallel Track Path (PTP),  Layer Type: recordable
	 Linear Density:         0,267 um/bit,  Track Density:  0,74 um/track
	 Starting Physical Sector Number of Data Area: 30000 h (DVD-ROM, DVD-R/-RW, DVD+R/+RW)
	 End Sector Number in Layer 0:                 0 h (LBN: FFFD0000 h, 4193920 MB)
	 Data in Burst Cutting Area (BCA) does not exist
	  Revision number of maximum recording speed: 6.0
	  Revision number of minimum recording speed: -
	  Revision number table of recording speed: 1.0 2.0 3.0 4.0 5.0 - - 
	  Class: 0
	  Start sector number of the current Border-Out: 2FE10 h
	  Start sector number of the next Border-In:     2FFA0 h
	 Media Specific [16..63]:
	    00 60 00 10 20 30 40 50 - 00 00 00 21 00 00 00 00    .`...0@P...!....
	    00 02 FE 10 00 02 FF A0 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	
17:49:48	#22 SCSI -400 File SCSIInterface.cpp, Line 366
	SCSI Exec, HA 0, TA 0, LUN 0
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x05 (0x0B, SCSI_TASTATUS_FAILED)
	Sense Key:  0x05 (KEY_ILLEGAL_REQUEST)
	Sense Code: 0x30
	Sense Qual: 0x05
	CDB Data:   0x53 0x00 0x00 0x00 0x00 0x00 0x05 0x7A 0xA0 0x00 
	Sense Data: 0x70 0x00 0x05 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x30 0x05 
	
17:49:48	#23 CDR -400 File ThreadedTransferInterface.cpp, Line 1750
	Unspecified target error
	_NEC DVD_RW ND-2500A (H:0 T:0)
	
17:49:48	#24 TRANSFER -27 File ThreadedTransferInterface.cpp, Line 1750
	Could not perform start of Disc-at-once
	
17:49:48	#25 Text 0 File ThreadedTransfer.cpp, Line 269
	Pipe memory size 83836800
	
17:49:48	#26 Phase 38 File ExtendedProgress.cpp, Line 537
	Burn process failed at 8x (11080 KB/s)
	

Can anyone help me on this...it keeps failing on me.

Cheers in advance.
Znort

---

### Post by loserboy on 2007-07-11
no clue about the error message, but you should try burning with a different program and see if it's hardware related, I recommend gnomebaker or k3b

---

### Post by Znort_Ubern00b on 2007-07-11
System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
_NEC DVD_RW ND-2500A 1.06 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

Burned media
-----------------------
DVD-R Sequential

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 1.0x1352KBps.
:-[ WRITE@LBA=0h failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:359065 -dvd-compat -speed=8 -use-the-force-luke=bufsize:32m 

This is the error message i get...

---

### Post by loserboy on 2007-07-11
are you sure those are blank discs?

do you have any other brand that you can try or borrow from someone

---

### Post by Znort_Ubern00b on 2007-07-11
yeah defo blanks, just bought them...Memorex. Don't have any others at the mo to try...

It recognises it as blank in Nero but then fails to write...

---

### Post by loserboy on 2007-07-11
ok I'm thinking it might be the discs though judging by the error that k3b threw out, especially since you just got them.

---

### Post by Znort_Ubern00b on 2007-07-12
Is there anyway that I can update so that the DVDs are recognised???

they are Memorex DVD-R up to 16x 4.7GB discs

or does anyone know of any discs that do work???

---

### Post by noynac on 2007-07-12
> **Znort_Ubern00b said:**
> Is there anyway that I can update so that the DVDs are recognised???

they are Memorex DVD-R up to 16x 4.7GB discs

or does anyone know of any discs that do work???

The Memorex (CMC) disks are not considered to be very good media. Verbatim DVD media is quite good. If I understand correctly, you have an NEC  2500A DVD writer, which is pretty old. You may want to check for firmware updates. 

Go to the forums at cdfreaks.com. This site has the official support forum for Nero Linux plus quite active forums for DVD writers.

---

