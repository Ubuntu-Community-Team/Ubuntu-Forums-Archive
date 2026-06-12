---
title: "Burn dvd+r from iso fails with LITE-ON DVDRW LDW-851S on 7.10 gutsy"
date: 2007-12-11
forum: General Help
---

### Post by [flax] on 2007-12-11
Hello,

I'm trying to burn a DVD's from iso's in gutsy, i'm currently at the point from where i don't know where to continue, and i refuse to install windows on my machine to burn a dvd.
I can  burn cd's in ubuntu, but i now wasted 7 dvd's so i only have 3 left and i really like to burn the iso

Steps i took after reading the ubuntuforums/bugtracker:
1 - I tried Brasero, which started doing something, but wasnt finished after 24 hours (first +/- 5 minutes the led burned red, then orange)
2 - Tried K3B but gave an error and does not continue past 0%
3 - Tried Nero, gave an error about /dev/sg0, fixed this with a sudo chown root:cdrom /dev/sg0 gives me the following error:
```

2CA0-7324-1800-2000-4077-1CEE-****

Linux 2.6.22-14-generic
Nero API version: 7.5.14.9
Using interface version: 7.5.1.2
Installed in: /usr/lib/nero/
Application: Nero AG\Nero Linux
Internal Version: 7, 5, 14, 9

Recorder:             <LITE-ON DVDRW LDW-851S>  Version: GS08 - HA 0 TA 0 - 0.0.0.0
 Adapter driver:      <ide-cdrom>               HA 0
 Drive buffer  :      2048kB
 Bus Type      :      default (0) -> ATAPI, detected: ?
Excluded drive IDs: 
WriteBufferSize: 83886080 (0) Byte
BUFE           : 0
Physical memory     : 1011MB (1035636kB)
Free physical memory: 93MB (96120kB)
Memory in use       : 90 %
Uncached PFiles: 0x0
Use Inquiry    : 1
Global Bus Type: default (0)
Check supported media : Disabled (0) 

11.12.2007
NeroAPI
19:26:24	#1 Text 0 File Burncd.cpp, Line 3490
	Turn on Disc-At-Once, using DVD media
	
19:26:25	#2 Text 0 File DlgWaitCD.cpp, Line 307
	Last possible write address on media:  2295103 (510:01.28, 4482MB)
	Last address to be written:            2294911 (509:58.61, 4482MB)
	
19:26:25	#3 Text 0 File DlgWaitCD.cpp, Line 319
	Write in overburning mode: NO
	
19:26:25	#4 Text 0 File DlgWaitCD.cpp, Line 2952
	Recorder: LITE-ON DVDRW LDW-851S, Media type: DVD+R
	 Disc Manufacturer ID: FTI, Media Type ID: 016, Product revision number: 0
	 Disc Application Code: 0, Extended Information Indicators: 7
	
19:26:25	#5 Text 0 File DlgWaitCD.cpp, Line 493
	>>> Protocol of DlgWaitCD activities: <<<
	=========================================
	
19:26:25	#6 Text 0 File ThreadedTransferInterface.cpp, Line 792
	Setup items (after recorder preparation)
	 0: TRM_DATA_MODE1 (2 - CD-ROM Mode 1)
	    2 indices, index0 (150) not provided
	    original disc pos #0 + 2294912 (2294912) = #2294912/509:58.62
	    not relocatable, disc pos for caching/writing not required/not required
	    -> TRM_DATA_MODE1, 2048, config 0, wanted index0 0 blocks, length 2294912 blocks [LITE-ON DVDRW LDW-851S (H:0 T:0)]
	--------------------------------------------------------------
	
19:26:25	#7 Text 0 File ThreadedTransferInterface.cpp, Line 995
	Prepare [LITE-ON DVDRW LDW-851S (H:0 T:0)] for write in CUE-sheet-DAO
	DAO infos:
	==========
	 MCN: ""
	 TOCType: 0x00; Session Closed, disc fixated
	 Tracks 1 to 1:                                  Idx 0         Idx 1      Next Trk
	   1: TRM_DATA_MODE1, 2048/0x00, FilePos             0             0    4699979776, ISRC ""
	DAO layout:
	===========
	 ___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
	        0 |  lead-in |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   1 |    0x41 |  2294912 |  2294912 | 0x00
	  2294912 | lead-out |   1 |    0x41 |        0 |        0 | 0x00
	
19:26:25	#8 Text 0 File Burncd.cpp, Line 4263
	Caching options: cache CDRom or Network-No, small files-Yes (<32KB)
	
19:26:25	#9 Phase 24 File ExtendedProgress.cpp, Line 537
	Caching of files started
	
19:26:25	#10 Text 0 File Burncd.cpp, Line 4382
	Cache writing successful.
	
19:26:25	#11 Phase 25 File ExtendedProgress.cpp, Line 537
	Caching of files completed
	
19:26:25	#12 Phase 36 File ExtendedProgress.cpp, Line 537
	Burn process started at 2,4x (3324 kB/sec)
	
19:26:25	#13 Text 0 File ThreadedTransferInterface.cpp, Line 2712
	Verifying disc position of item 0 (not relocatable, no disc pos, no patch infos, orig at #0): write at #0
	
19:26:25	#14 Text 0 File Cdrdrv.cpp, Line 9915
	---- Disc Structure: Physical Format Information (00h) ----
	Media Type: 0, Layer: 0, Address: 0 (0 h), AGID: 0; Length: 2050
	 Book Type: DVD+R (10), Part Version: 1.0x (1)
	 Disc Size: 120 mm,      Maximum Rate: <not specified> (F h)
	 Number of Layers: 1,    Track Path: Parallel Track Path (PTP),  Layer Type: recordable
	 Linear Density:         0,267 um/bit,  Track Density:  0,74 um/track
	 Starting Physical Sector Number of Data Area: 30000 h (DVD-ROM, DVD-R/-RW, DVD+R/+RW)
	 End Sector Number in Layer 0:                 0 h (LBN: FFFD0000 h, 4193920 MB)
	 Data in Burst Cutting Area (BCA) does not exist
	  Disc Application Code: 0 / 0 h
	  Extended Information indicators: 7 h
	  Disc Manufacturer ID: FTI.....
	  Media type ID: 016
	  Product revision number: 0
	  Number of Physical format information bytes in use in ADIP up to byte 63: 56
	 Media Specific [16..63]:
	    00 00 07 46 54 49 00 00 - 00 00 00 30 31 36 00 38    ...FTI.....016.8
	    23 54 37 12 02 54 6C 02 - 92 5F 15 15 0B 0B 08 08    #T7..Tl.._......
	    01 19 1B 0C 0C 0C 0D 01 - 00 00 00 00 00 00 00 00    ................
	
19:26:25	#15 Text 0 File DVDPlusRW.cpp, Line 675
	Start write address at LBA 0
	DVD high compatibility mode: Yes
	
19:26:25	#16 Text 0 File ThreadedTransfer.cpp, Line 269
	Pipe memory size 83836800
	
19:31:23	#17 SCSI -1135 File SCSIInterface.cpp, Line 622
	SCSI Exec, HA 0, TA 0, LUN 0, buffer 0x0xab4e2c80
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x02 (0x01, SCSI_TASTATUS_CHKCOND)
	Sense Key:  0x03 (KEY_MEDIUM_ERROR)
	Sense Code: 0x0C
	Sense Qual: 0x00
	CDB Data:   0x2A 0x00 0x00 0x00 0x16 0x20 0x00 0x00 0x20 0x00 0x00 0x00 
	Sense Data: 0x71 0x00 0x03 0x00 0x00 0x00 0x00 0x0A 
	            0x00 0x00 0x00 0x00 0x0C 0x00 
	
19:31:23	#18 CDR -1135 File Writer.cpp, Line 299
	Write error
	LITE-ON DVDRW LDW-851S (H:0 T:0)
	
19:31:23	#19 Phase 127 File ExtendedProgress.cpp, Line 537
	Generating DVD high compatibility borders
	
19:31:23	#20 Text 0 File DVDPlusRW.cpp, Line 935
	EndDAO: Last written address 5664
	
19:31:23	#21 Phase 129 File ExtendedProgress.cpp, Line 537
	Generating DVD borders completed successfully
	
19:31:24	#22 Phase 38 File ExtendedProgress.cpp, Line 537
	Burn process failed at 2,4x (3324 kB/sec)	

```

4 - Tried growisofs:
```

merel@eduard-desktop:~$ sudo -Z /dev/hdc=burn.iso 
Executing 'builtin_dd if=burn.iso of=/dev/hdc obs=32k seek=0'
/dev/hdc: "Current Write Speed" is 2.5x1352KBps.
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.8% UBU   0.0%
   10813440/4699979776 ( 0.2%) @2.3x, remaining 361:22 RBU 100.0% UBU  81.0%
   21659648/4699979776 ( 0.5%) @2.3x, remaining 194:23 RBU 100.0% UBU  99.3%
   32473088/4699979776 ( 0.7%) @2.3x, remaining 136:32 RBU 100.0% UBU  99.4%
   43286528/4699979776 ( 0.9%) @2.3x, remaining 107:34 RBU 100.0% UBU  99.4%
   54198272/4699979776 ( 1.2%) @2.4x, remaining 91:25 RBU 100.0% UBU  99.3%
:-[ WRITE@LBA=6fb0h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
:-( write failed: Input/output error
/dev/hdc: flushing cache
/dev/hdc: closing track
/dev/hdc: closing session
/dev/hdc: reloading tray

```
```

merel@eduard-desktop:~$ sudo cat /var/log/messages
....
....
Dec 11 22:13:16 eduard-desktop kernel: [30405.901303] cdrom: This disc doesn't have any tracks I recognize!
Dec 11 22:13:16 eduard-desktop kernel: [30405.953176] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Dec 11 22:13:16 eduard-desktop kernel: [30405.953184] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Dec 11 22:13:16 eduard-desktop kernel: [30405.953188] ide: failed opcode was: unknown
Dec 11 22:13:16 eduard-desktop kernel: [30405.953515] end_request: I/O error, dev hdc, sector 0
Dec 11 22:13:16 eduard-desktop kernel: [30405.954585] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Dec 11 22:13:16 eduard-desktop kernel: [30405.954591] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Dec 11 22:13:16 eduard-desktop kernel: [30405.954594] ide: failed opcode was: unknown
Dec 11 22:13:16 eduard-desktop kernel: [30405.954918] end_request: I/O error, dev hdc, sector 0
Dec 11 22:13:16 eduard-desktop kernel: [30405.955480] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Dec 11 22:13:16 eduard-desktop kernel: [30405.955485] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Dec 11 22:13:16 eduard-desktop kernel: [30405.955488] ide: failed opcode was: unknown
Dec 11 22:13:16 eduard-desktop kernel: [30405.955813] end_request: I/O error, dev hdc, sector 4
Dec 11 22:13:16 eduard-desktop kernel: [30405.956695] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Dec 11 22:13:16 eduard-desktop kernel: [30405.956700] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Dec 11 22:13:16 eduard-desktop kernel: [30405.956703] ide: failed opcode was: unknown
...
...
...
Dec 11 22:13:16 eduard-desktop kernel: [30406.011721] end_request: I/O error, dev hdc, sector 4
Dec 11 22:13:16 eduard-desktop kernel: [30406.012399] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Dec 11 22:13:16 eduard-desktop kernel: [30406.012404] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Dec 11 22:13:16 eduard-desktop kernel: [30406.012407] ide: failed opcode was: unknown
Dec 11 22:13:16 eduard-desktop kernel: [30406.012731] end_request: I/O error, dev hdc, sector 0
Dec 11 22:13:16 eduard-desktop kernel: [30406.013294] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Dec 11 22:13:16 eduard-desktop kernel: [30406.013299] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Dec 11 22:13:16 eduard-desktop kernel: [30406.013302] ide: failed opcode was: unknown
Dec 11 22:13:16 eduard-desktop kernel: [30406.013627] end_request: I/O error, dev hdc, sector 4
Dec 11 22:13:16 eduard-desktop kernel: [30406.028078] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Dec 11 22:13:16 eduard-desktop kernel: [30406.028086] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Dec 11 22:13:16 eduard-desktop kernel: [30406.028090] ide: failed opcode was: unknown
Dec 11 22:13:16 eduard-desktop kernel: [30406.028446] end_request: I/O error, dev hdc, sector 0
Dec 11 22:13:16 eduard-desktop kernel: [30406.029008] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Dec 11 22:13:16 eduard-desktop kernel: [30406.029013] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Dec 11 22:13:16 eduard-desktop kernel: [30406.029017] ide: failed opcode was: unknown
Dec 11 22:13:16 eduard-desktop kernel: [30406.029342] end_request: I/O error, dev hdc, sector 4
Dec 11 22:13:16 eduard-desktop kernel: [30406.030830] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Dec 11 22:13:16 eduard-desktop kernel: [30406.030835] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Dec 11 22:13:16 eduard-desktop kernel: [30406.030839] ide: failed opcode was: unknown
Dec 11 22:13:16 eduard-desktop kernel: [30406.031165] end_request: I/O error, dev hdc, sector 0
Dec 11 22:13:16 eduard-desktop kernel: [30406.031727] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Dec 11 22:13:16 eduard-desktop kernel: [30406.031732] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Dec 11 22:13:16 eduard-desktop kernel: [30406.031735] ide: failed opcode was: unknown
Dec 11 22:13:16 eduard-desktop kernel: [30406.032074] end_request: I/O error, dev hdc, sector 4

```

ps: i also used: hdparm -d1 -c1 -a8 -u1 -Xmdma1 /dev/hdc

---

### Post by KiXeR on 2007-12-12
Maybe this will help!

[http://www.webservertalk.com/archive238-2005-3-945131.html](http://www.webservertalk.com/archive238-2005-3-945131.html)

/K

---

### Post by [flax] on 2007-12-12
KiXeR,

Thank you for your post, but i don't have any problems using the dvd for reading data. 

Maybe you want to point anything out with the link you send me, but i don't understand what you are trying to say. Or you are suggesting that:
? - i try to burn a regio bound iso, which is read during the burning proces and causes a regio problem?
? - the dvdburner is broken?

---

### Post by [flax] on 2007-12-13
Could somebody give me some pointers? Otherwise i guess i have to post it as a bug?

---

### Post by Lostincyberspace on 2007-12-13
Try using k3b to burn and post the exact error. a screen shot would be the best.

---

### Post by [flax] on 2007-12-13
The error/debug log of K3B is the following:
```

System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
JLMS XJ-HD166S DS1A (/dev/hdd, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]

LITE-ON DVDRW LDW-851S GS08 (/dev/hdc, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-RW, DVD+R, DVD+RW] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]
Burned media
-----------------------
DVD+R

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdc obs=32k seek=0'
/dev/hdc: "Current Write Speed" is 2.5x1352KBps.
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
    4325376/4699979776 ( 0.1%) @0.9x, remaining 687:33 RBU 100.0% UBU  65.6%
    7110656/4699979776 ( 0.2%) @0.6x, remaining 461:59 RBU 100.0% UBU  99.7%
:-[ WRITE@LBA=d90h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
:-( write failed: Input/output error
/dev/hdc: flushing cache
/dev/hdc: closing track
/dev/hdc: closing disc

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/hdc=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2294912 -dvd-compat -speed=2.4 -use-the-force-luke=bufsize:32m 


```

---

### Post by [flax] on 2007-12-13
The following screenshot after K3B fails: [http://nergens.org/k3b.png](http://nergens.org/k3b.png)

---

### Post by [flax] on 2007-12-14
Can somebody give me some more pointers or help what to do next?

---

### Post by geraldm on 2007-12-14
This is unrelated to the problem, as the write fail comes too early, but I am curious about the filesystem named "burn.iso"
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
If it is 4,699,979,776 bytes then it is too big for iso9660, and the filesystem type must be udf.
iso9660 filesystems have an integer overflow points at 2G and 4G.
There is a wikipedia article on "iso9660" which mentions the size issues.

Gerald

---

### Post by Craigus on 2007-12-14
The drive may be faulty. On way to test would be to download a linux live CD that has a copy to ram option - knoppix is one. You can boot, remove the CD and then try burning a DVD. You do need a reasonable amount of memory to do this with knoppix, but there are other, lighter distros that will do it as well.

---

### Post by [flax] on 2007-12-15
Hello,

What i do remeber is that i never burned dvd's under linux, because it gave me errors and i always used nero under windows, however i dont have windows anymore installed to do a test with nero under windows.

I took the following steps: 
1- Burned the knoppix 5.1.0 iso on a recordable cd (with the drive)
2- Boot from the knoppix cdrom, with toram option
3- When i wanted to burn the iso, i removed the cdrom and inserted the dvd then the system froze
Well after this i put the cdrom into the (other)cdplayer and took the following steps:
1- Booted with no additional options
2- Started k3b and started burning the iso.  (at a speed of 1x, i will now test this also under ubuntu)
This was a lot more succesfull than under ubuntu, only it also gave an error:
```

System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.7
Kernel:      2.6.19
Devices
-----------------------
LITE-ON DVDRW LDW-851S GS08 (/dev/hdc, ) at /media/hdc [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RW; DVD+R; DVD+RW] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

JLMS XJ-HD166S DS1A (/dev/hdd, ) at /media/hdd [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]
Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/media/sda3/eduard/Bureaublad/wii.iso of=/dev/hdc obs=32k seek=0'
/dev/hdc: "Current Write Speed" is 2.5x1352KBps.
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
    3637248/4699979776 ( 0.1%) @0.8x, remaining 925:20 RBU 100.0% UBU  78.0%
   14385152/4699979776 ( 0.3%) @2.3x, remaining 255:09 RBU 100.0% UBU  99.7%
   25165824/4699979776 ( 0.5%) @2.3x, remaining 154:48 RBU 100.0% UBU  99.7%
   35880960/4699979776 ( 0.8%) @2.3x, remaining 114:49 RBU 100.0% UBU  99.3%
   46661632/4699979776 ( 1.0%) @2.3x, remaining 94:44 RBU 100.0% UBU  99.7%
   57442304/4699979776 ( 1.2%) @2.3x, remaining 80:49 RBU 100.0% UBU  99.7%
   68190208/4699979776 ( 1.5%) @2.3x, remaining 71:19 RBU 100.0% UBU  99.7%
   79003648/4699979776 ( 1.7%) @2.3x, remaining 65:18 RBU 100.0% UBU  99.7%
   89784320/4699979776 ( 1.9%) @2.3x, remaining 59:54 RBU 100.0% UBU  99.7%
  100532224/4699979776 ( 2.1%) @2.3x, remaining 55:39 RBU 100.0% UBU  99.7%
  111345664/4699979776 ( 2.4%) @2.4x, remaining 52:53 RBU 100.0% UBU  99.3%
  122093568/4699979776 ( 2.6%) @2.3x, remaining 49:59 RBU 100.0% UBU  99.7%
  132841472/4699979776 ( 2.8%) @2.3x, remaining 47:33 RBU 100.0% UBU  99.7%
  143622144/4699979776 ( 3.1%) @2.3x, remaining 46:00 RBU 100.0% UBU  99.7%
  153485312/4699979776 ( 3.3%) @2.1x, remaining 44:25 RBU 100.0% UBU  99.7%
  165183488/4699979776 ( 3.5%) @2.6x, remaining 42:33 RBU 100.0% UBU  99.7%
  175996928/4699979776 ( 3.7%) @2.3x, remaining 41:07 RBU 100.0% UBU  99.7%
  186744832/4699979776 ( 4.0%) @2.3x, remaining 40:16 RBU 100.0% UBU  99.7%
  197558272/4699979776 ( 4.2%) @2.3x, remaining 39:07 RBU 100.0% UBU  99.7%
  208404480/4699979776 ( 4.4%) @2.4x, remaining 38:04 RBU 100.0% UBU  99.7%
  219185152/4699979776 ( 4.7%) @2.3x, remaining 37:28 RBU 100.0% UBU  99.7%
  229965824/4699979776 ( 4.9%) @2.3x, remaining 36:36 RBU 100.0% UBU  99.7%
  240779264/4699979776 ( 5.1%) @2.3x, remaining 35:48 RBU 100.0% UBU  99.7%
  251559936/4699979776 ( 5.4%) @2.3x, remaining 35:22 RBU 100.0% UBU  99.7%
  262373376/4699979776 ( 5.6%) @2.3x, remaining 34:40 RBU 100.0% UBU  99.7%
  273186816/4699979776 ( 5.8%) @2.4x, remaining 34:01 RBU 100.0% UBU  99.7%
  283967488/4699979776 ( 6.0%) @2.3x, remaining 33:41 RBU 100.0% UBU  99.6%
  294748160/4699979776 ( 6.3%) @2.3x, remaining 33:07 RBU 100.0% UBU  99.7%
  305561600/4699979776 ( 6.5%) @2.3x, remaining 32:35 RBU 100.0% UBU  99.7%
  316342272/4699979776 ( 6.7%) @2.3x, remaining 32:20 RBU 100.0% UBU  99.7%
  327024640/4699979776 ( 7.0%) @2.3x, remaining 31:52 RBU 100.0% UBU  99.7%
  337838080/4699979776 ( 7.2%) @2.4x, remaining 31:25 RBU 100.0% UBU  99.7%
  348618752/4699979776 ( 7.4%) @2.3x, remaining 31:12 RBU 100.0% UBU  99.7%
  359366656/4699979776 ( 7.6%) @2.3x, remaining 30:48 RBU 100.0% UBU  99.7%
  370180096/4699979776 ( 7.9%) @2.3x, remaining 30:24 RBU 100.0% UBU  99.7%
  380960768/4699979776 ( 8.1%) @2.3x, remaining 30:13 RBU 100.0% UBU  99.7%
  391741440/4699979776 ( 8.3%) @2.3x, remaining 29:52 RBU 100.0% UBU  99.7%
  402522112/4699979776 ( 8.6%) @2.3x, remaining 29:32 RBU 100.0% UBU  99.7%
  413270016/4699979776 ( 8.8%) @2.3x, remaining 29:23 RBU 100.0% UBU  99.7%
  424050688/4699979776 ( 9.0%) @2.3x, remaining 29:04 RBU 100.0% UBU  99.7%
  434896896/4699979776 ( 9.3%) @2.4x, remaining 28:46 RBU 100.0% UBU  99.7%
  445710336/4699979776 ( 9.5%) @2.3x, remaining 28:38 RBU 100.0% UBU  99.7%
  456523776/4699979776 ( 9.7%) @2.3x, remaining 28:21 RBU 100.0% UBU  99.7%
  467337216/4699979776 ( 9.9%) @2.3x, remaining 28:04 RBU 100.0% UBU  99.7%
  478117888/4699979776 (10.2%) @2.3x, remaining 27:48 RBU 100.0% UBU  99.7%
  488964096/4699979776 (10.4%) @2.3x, remaining 27:42 RBU 100.0% UBU  99.7%
  499712000/4699979776 (10.6%) @2.3x, remaining 27:27 RBU 100.0% UBU  99.7%
  510459904/4699979776 (10.9%) @2.3x, remaining 27:13 RBU 100.0% UBU  99.7%
  521240576/4699979776 (11.1%) @2.3x, remaining 27:07 RBU 100.0% UBU  99.7%
  532021248/4699979776 (11.3%) @2.4x, remaining 26:53 RBU 100.0% UBU  99.7%
  542867456/4699979776 (11.6%) @2.4x, remaining 26:40 RBU 100.0% UBU  99.7%
  553615360/4699979776 (11.8%) @2.3x, remaining 26:35 RBU 100.0% UBU  99.7%
  564428800/4699979776 (12.0%) @2.4x, remaining 26:22 RBU  99.6% UBU  99.7%
  575209472/4699979776 (12.2%) @2.3x, remaining 26:10 RBU 100.0% UBU  99.7%
  586055680/4699979776 (12.5%) @2.3x, remaining 26:05 RBU 100.0% UBU  99.7%
  596869120/4699979776 (12.7%) @2.3x, remaining 25:53 RBU 100.0% UBU  99.7%
  607682560/4699979776 (12.9%) @2.4x, remaining 25:42 RBU  99.6% UBU  99.7%
  618430464/4699979776 (13.2%) @2.3x, remaining 25:37 RBU 100.0% UBU  99.7%
  629243904/4699979776 (13.4%) @2.4x, remaining 25:26 RBU 100.0% UBU  99.7%
  639991808/4699979776 (13.6%) @2.3x, remaining 25:16 RBU 100.0% UBU  99.7%
  650772480/4699979776 (13.8%) @2.3x, remaining 25:11 RBU 100.0% UBU  99.7%
  661618688/4699979776 (14.1%) @2.4x, remaining 25:01 RBU 100.0% UBU  99.7%
  672366592/4699979776 (14.3%) @2.3x, remaining 24:51 RBU 100.0% UBU  99.7%
  683180032/4699979776 (14.5%) @2.3x, remaining 24:47 RBU 100.0% UBU  99.7%
  693993472/4699979776 (14.8%) @2.4x, remaining 24:37 RBU 100.0% UBU  99.7%
  704774144/4699979776 (15.0%) @2.3x, remaining 24:28 RBU 100.0% UBU  99.7%
  715554816/4699979776 (15.2%) @2.4x, remaining 24:24 RBU 100.0% UBU  99.7%
  726335488/4699979776 (15.5%) @2.4x, remaining 24:15 RBU 100.0% UBU  99.7%
  737116160/4699979776 (15.7%) @2.3x, remaining 24:06 RBU 100.0% UBU  99.7%
  747896832/4699979776 (15.9%) @2.3x, remaining 23:57 RBU 100.0% UBU  99.7%
  758710272/4699979776 (16.1%) @2.4x, remaining 23:53 RBU 100.0% UBU  99.7%
  769556480/4699979776 (16.4%) @2.4x, remaining 23:44 RBU 100.0% UBU  99.7%
  780369920/4699979776 (16.6%) @2.3x, remaining 23:36 RBU 100.0% UBU  99.7%
  791183360/4699979776 (16.8%) @2.3x, remaining 23:32 RBU 100.0% UBU  99.7%
  801996800/4699979776 (17.1%) @2.4x, remaining 23:24 RBU 100.0% UBU  99.7%
  812843008/4699979776 (17.3%) @2.4x, remaining 23:16 RBU 100.0% UBU  99.7%
  823623680/4699979776 (17.5%) @2.3x, remaining 23:13 RBU 100.0% UBU  99.7%
  834404352/4699979776 (17.8%) @2.4x, remaining 23:05 RBU 100.0% UBU  99.7%
  845217792/4699979776 (18.0%) @2.3x, remaining 22:57 RBU 100.0% UBU  99.7%
  856031232/4699979776 (18.2%) @2.4x, remaining 22:54 RBU 100.0% UBU  99.7%
  866910208/4699979776 (18.4%) @2.4x, remaining 22:46 RBU 100.0% UBU  99.7%
  877690880/4699979776 (18.7%) @2.4x, remaining 22:38 RBU 100.0% UBU  99.7%
  888504320/4699979776 (18.9%) @2.4x, remaining 22:35 RBU 100.0% UBU  99.7%
  899284992/4699979776 (19.1%) @2.3x, remaining 22:28 RBU 100.0% UBU  99.7%
  910131200/4699979776 (19.4%) @2.4x, remaining 22:20 RBU 100.0% UBU  99.7%
  920944640/4699979776 (19.6%) @2.3x, remaining 22:17 RBU 100.0% UBU  99.7%
  931758080/4699979776 (19.8%) @2.4x, remaining 22:10 RBU 100.0% UBU  99.7%
  942571520/4699979776 (20.1%) @2.3x, remaining 22:03 RBU 100.0% UBU  99.7%
  953384960/4699979776 (20.3%) @2.4x, remaining 22:00 RBU 100.0% UBU  99.7%
  964231168/4699979776 (20.5%) @2.4x, remaining 21:53 RBU 100.0% UBU  99.7%
  975077376/4699979776 (20.7%) @2.4x, remaining 21:46 RBU 100.0% UBU  99.7%
  985890816/4699979776 (21.0%) @2.3x, remaining 21:43 RBU 100.0% UBU  99.7%
  996704256/4699979776 (21.2%) @2.4x, remaining 21:36 RBU 100.0% UBU  99.7%
 1007550464/4699979776 (21.4%) @2.3x, remaining 21:29 RBU 100.0% UBU  99.7%
 1018363904/4699979776 (21.7%) @2.3x, remaining 21:27 RBU 100.0% UBU  99.7%
 1029177344/4699979776 (21.9%) @2.4x, remaining 21:20 RBU 100.0% UBU  99.7%
 1039958016/4699979776 (22.1%) @2.3x, remaining 21:14 RBU 100.0% UBU  99.7%
 1050836992/4699979776 (22.4%) @2.4x, remaining 21:10 RBU 100.0% UBU  99.7%
 1061650432/4699979776 (22.6%) @2.4x, remaining 21:04 RBU 100.0% UBU  99.7%
 1072463872/4699979776 (22.8%) @2.4x, remaining 20:58 RBU 100.0% UBU  99.7%
 1083244544/4699979776 (23.0%) @2.4x, remaining 20:52 RBU 100.0% UBU  99.7%
 1094090752/4699979776 (23.3%) @2.4x, remaining 20:49 RBU 100.0% UBU  99.7%
 1104871424/4699979776 (23.5%) @2.3x, remaining 20:42 RBU 100.0% UBU  99.7%
 1115684864/4699979776 (23.7%) @2.3x, remaining 20:36 RBU 100.4% UBU  99.7%
 1126498304/4699979776 (24.0%) @2.4x, remaining 20:33 RBU 100.0% UBU  99.7%
 1137344512/4699979776 (24.2%) @2.4x, remaining 20:27 RBU 100.0% UBU  99.7%
 1148223488/4699979776 (24.4%) @2.4x, remaining 20:21 RBU 100.0% UBU  99.7%
 1159036928/4699979776 (24.7%) @2.4x, remaining 20:18 RBU 100.0% UBU  99.7%
 1169883136/4699979776 (24.9%) @2.4x, remaining 20:13 RBU 100.0% UBU  99.7%
 1180696576/4699979776 (25.1%) @2.4x, remaining 20:07 RBU 100.0% UBU  99.7%
 1191542784/4699979776 (25.4%) @2.3x, remaining 20:04 RBU 100.0% UBU  99.7%
 1202388992/4699979776 (25.6%) @2.3x, remaining 19:58 RBU 100.0% UBU  99.7%
 1213235200/4699979776 (25.8%) @2.4x, remaining 19:52 RBU 100.0% UBU  99.7%
 1224015872/4699979776 (26.0%) @2.3x, remaining 19:49 RBU 100.0% UBU  99.7%
 1234829312/4699979776 (26.3%) @2.4x, remaining 19:44 RBU 100.0% UBU  99.6%
 1245642752/4699979776 (26.5%) @2.4x, remaining 19:38 RBU 100.0% UBU  99.7%
 1256456192/4699979776 (26.7%) @2.4x, remaining 19:35 RBU 100.0% UBU  99.7%
 1267269632/4699979776 (27.0%) @2.3x, remaining 19:30 RBU 100.0% UBU  99.7%
 1278148608/4699979776 (27.2%) @2.4x, remaining 19:24 RBU 100.0% UBU  99.6%
 1288994816/4699979776 (27.4%) @2.4x, remaining 19:21 RBU 100.0% UBU  99.7%
 1299775488/4699979776 (27.7%) @2.4x, remaining 19:16 RBU 100.0% UBU  99.7%
 1310588928/4699979776 (27.9%) @2.4x, remaining 19:10 RBU 100.0% UBU  99.7%
 1321402368/4699979776 (28.1%) @2.4x, remaining 19:08 RBU 100.0% UBU  99.7%
 1332248576/4699979776 (28.3%) @2.3x, remaining 19:02 RBU 100.0% UBU  99.7%
 1343094784/4699979776 (28.6%) @2.4x, remaining 18:57 RBU 100.0% UBU  99.7%
 1353940992/4699979776 (28.8%) @2.4x, remaining 18:54 RBU 100.0% UBU  99.7%
 1364787200/4699979776 (29.0%) @2.4x, remaining 18:49 RBU 100.0% UBU  99.7%
 1375666176/4699979776 (29.3%) @2.4x, remaining 18:43 RBU 100.0% UBU  99.7%
 1386479616/4699979776 (29.5%) @2.4x, remaining 18:40 RBU 100.0% UBU  99.7%
 1397325824/4699979776 (29.7%) @2.4x, remaining 18:35 RBU 100.0% UBU  99.7%
 1408106496/4699979776 (30.0%) @2.4x, remaining 18:30 RBU 100.0% UBU  99.7%
 1418919936/4699979776 (30.2%) @2.4x, remaining 18:27 RBU 100.0% UBU  99.7%
 1429798912/4699979776 (30.4%) @2.4x, remaining 18:22 RBU 100.0% UBU  99.7%
 1440612352/4699979776 (30.7%) @2.4x, remaining 18:17 RBU 100.0% UBU  99.7%
 1451458560/4699979776 (30.9%) @2.4x, remaining 18:12 RBU 100.0% UBU  99.7%
 1462337536/4699979776 (31.1%) @2.4x, remaining 18:09 RBU 100.0% UBU  99.7%
 1473150976/4699979776 (31.3%) @2.4x, remaining 18:04 RBU 100.0% UBU  99.7%
 1484029952/4699979776 (31.6%) @2.4x, remaining 17:59 RBU 100.0% UBU  99.7%
 1494843392/4699979776 (31.8%) @2.4x, remaining 17:56 RBU 100.0% UBU  99.7%
 1505689600/4699979776 (32.0%) @2.4x, remaining 17:51 RBU 100.0% UBU  99.7%
 1516535808/4699979776 (32.3%) @2.4x, remaining 17:46 RBU 100.0% UBU  99.7%
 1527316480/4699979776 (32.5%) @2.4x, remaining 17:43 RBU 100.0% UBU  99.7%
 1538162688/4699979776 (32.7%) @2.4x, remaining 17:38 RBU 100.0% UBU  99.6%
 1549008896/4699979776 (33.0%) @2.4x, remaining 17:33 RBU 100.0% UBU  99.7%
 1559855104/4699979776 (33.2%) @2.4x, remaining 17:30 RBU 100.0% UBU  99.7%
 1570668544/4699979776 (33.4%) @2.4x, remaining 17:25 RBU 100.0% UBU  99.7%
 1581514752/4699979776 (33.6%) @2.4x, remaining 17:21 RBU 100.0% UBU  99.7%
 1592360960/4699979776 (33.9%) @2.4x, remaining 17:18 RBU 100.0% UBU  99.7%
 1603141632/4699979776 (34.1%) @2.4x, remaining 17:13 RBU 100.0% UBU  99.7%
 1613987840/4699979776 (34.3%) @2.4x, remaining 17:08 RBU 100.0% UBU  99.7%
 1624801280/4699979776 (34.6%) @2.4x, remaining 17:05 RBU 100.0% UBU  99.7%
 1635647488/4699979776 (34.8%) @2.4x, remaining 17:01 RBU  99.6% UBU  99.7%
 1646395392/4699979776 (35.0%) @2.4x, remaining 16:56 RBU 100.0% UBU  99.7%
 1657274368/4699979776 (35.3%) @2.4x, remaining 16:53 RBU 100.0% UBU  99.7%
 1668087808/4699979776 (35.5%) @2.4x, remaining 16:48 RBU 100.0% UBU  99.7%
 1678934016/4699979776 (35.7%) @2.4x, remaining 16:44 RBU 100.0% UBU  99.7%
 1689780224/4699979776 (36.0%) @2.4x, remaining 16:41 RBU 100.0% UBU  99.7%
 1700659200/4699979776 (36.2%) @2.4x, remaining 16:36 RBU 100.0% UBU  99.7%
 1711505408/4699979776 (36.4%) @2.4x, remaining 16:31 RBU 100.0% UBU  99.7%
 1722286080/4699979776 (36.6%) @2.4x, remaining 16:28 RBU 100.0% UBU  99.7%
 1733165056/4699979776 (36.9%) @2.4x, remaining 16:24 RBU 100.0% UBU  99.7%
 1743978496/4699979776 (37.1%) @2.4x, remaining 16:19 RBU 100.0% UBU  99.7%
 1754824704/4699979776 (37.3%) @2.4x, remaining 16:15 RBU 100.0% UBU  99.7%
 1765670912/4699979776 (37.6%) @2.4x, remaining 16:12 RBU 100.0% UBU  99.7%
 1776517120/4699979776 (37.8%) @2.4x, remaining 16:07 RBU 100.0% UBU  99.7%
 1787330560/4699979776 (38.0%) @2.4x, remaining 16:03 RBU 100.0% UBU  99.7%
 1798209536/4699979776 (38.3%) @2.4x, remaining 16:00 RBU 100.0% UBU  99.7%
 1809022976/4699979776 (38.5%) @2.4x, remaining 15:55 RBU 100.0% UBU  99.7%
 1819869184/4699979776 (38.7%) @2.4x, remaining 15:51 RBU 100.0% UBU  99.7%
 1830715392/4699979776 (39.0%) @2.4x, remaining 15:48 RBU 100.0% UBU  99.7%
 1841496064/4699979776 (39.2%) @2.4x, remaining 15:43 RBU 100.0% UBU  99.7%
 1852375040/4699979776 (39.4%) @2.4x, remaining 15:39 RBU 100.0% UBU  99.7%
 1863221248/4699979776 (39.6%) @2.4x, remaining 15:36 RBU 100.0% UBU  99.7%
 1874067456/4699979776 (39.9%) @2.4x, remaining 15:31 RBU 100.0% UBU  99.7%
 1884946432/4699979776 (40.1%) @2.4x, remaining 15:27 RBU 100.0% UBU  99.6%
 1895759872/4699979776 (40.3%) @2.4x, remaining 15:24 RBU 100.0% UBU  99.7%
 1906606080/4699979776 (40.6%) @2.4x, remaining 15:20 RBU 100.0% UBU  99.7%
 1917485056/4699979776 (40.8%) @2.4x, remaining 15:15 RBU 100.0% UBU  99.7%
 1928331264/4699979776 (41.0%) @2.4x, remaining 15:12 RBU 100.0% UBU  99.7%
 1939210240/4699979776 (41.3%) @2.4x, remaining 15:08 RBU 100.0% UBU  99.7%
 1949990912/4699979776 (41.5%) @2.4x, remaining 15:03 RBU 100.0% UBU  99.7%
 1960837120/4699979776 (41.7%) @2.4x, remaining 15:01 RBU 100.0% UBU  99.7%
 1971683328/4699979776 (42.0%) @2.4x, remaining 14:56 RBU 100.0% UBU  99.7%
 1982529536/4699979776 (42.2%) @2.4x, remaining 14:52 RBU 100.0% UBU  99.7%
 1993375744/4699979776 (42.4%) @2.4x, remaining 14:49 RBU  99.6% UBU  99.7%
 2004189184/4699979776 (42.6%) @2.4x, remaining 14:45 RBU 100.0% UBU  99.7%
 2015035392/4699979776 (42.9%) @2.4x, remaining 14:40 RBU 100.0% UBU  99.7%
 2025848832/4699979776 (43.1%) @2.4x, remaining 14:37 RBU 100.0% UBU  99.7%
 2036727808/4699979776 (43.3%) @2.4x, remaining 14:33 RBU 100.0% UBU  98.2%
 2047574016/4699979776 (43.6%) @2.4x, remaining 14:29 RBU 100.0% UBU  99.7%
 2058354688/4699979776 (43.8%) @2.4x, remaining 14:24 RBU 100.0% UBU  99.7%
 2069233664/4699979776 (44.0%) @2.4x, remaining 14:21 RBU 100.0% UBU  99.7%
 2080079872/4699979776 (44.3%) @2.4x, remaining 14:17 RBU 100.0% UBU  99.7%
 2090991616/4699979776 (44.5%) @2.4x, remaining 14:13 RBU  99.6% UBU  99.7%
 2101837824/4699979776 (44.7%) @2.4x, remaining 14:10 RBU 100.0% UBU  99.7%
 2112684032/4699979776 (45.0%) @2.4x, remaining 14:06 RBU 100.0% UBU  99.7%
 2123563008/4699979776 (45.2%) @2.4x, remaining 14:01 RBU 100.0% UBU  99.7%
 2134409216/4699979776 (45.4%) @2.4x, remaining 13:58 RBU 100.0% UBU  99.7%
 2145255424/4699979776 (45.6%) @2.4x, remaining 13:54 RBU 100.0% UBU  99.7%
 2156101632/4699979776 (45.9%) @2.4x, remaining 13:50 RBU 100.0% UBU  99.7%
 2166947840/4699979776 (46.1%) @2.4x, remaining 13:47 RBU 100.0% UBU  99.7%
 2177794048/4699979776 (46.3%) @2.4x, remaining 13:43 RBU 100.0% UBU  99.7%
 2188640256/4699979776 (46.6%) @2.4x, remaining 13:39 RBU 100.0% UBU  99.7%
 2199519232/4699979776 (46.8%) @2.4x, remaining 13:36 RBU 100.0% UBU  99.7%
 2210299904/4699979776 (47.0%) @2.4x, remaining 13:32 RBU 100.0% UBU  99.7%
 2221146112/4699979776 (47.3%) @2.4x, remaining 13:27 RBU 100.0% UBU  99.7%
 2232025088/4699979776 (47.5%) @2.4x, remaining 13:24 RBU 100.0% UBU  99.7%
 2242871296/4699979776 (47.7%) @2.4x, remaining 13:20 RBU 100.0% UBU  99.7%
 2253717504/4699979776 (48.0%) @2.4x, remaining 13:16 RBU 100.0% UBU  99.7%
 2264530944/4699979776 (48.2%) @2.4x, remaining 13:13 RBU 100.0% UBU  99.7%
 2275377152/4699979776 (48.4%) @2.4x, remaining 13:09 RBU 100.0% UBU  99.7%
 2286223360/4699979776 (48.6%) @2.4x, remaining 13:05 RBU 100.0% UBU  99.7%
 2297069568/4699979776 (48.9%) @2.4x, remaining 13:02 RBU 100.0% UBU  99.7%
 2307915776/4699979776 (49.1%) @2.4x, remaining 12:58 RBU  99.6% UBU  99.7%
 2318761984/4699979776 (49.3%) @2.4x, remaining 12:54 RBU 100.0% UBU  99.7%
 2329608192/4699979776 (49.6%) @2.4x, remaining 12:51 RBU 100.0% UBU  99.7%
 2340421632/4699979776 (49.8%) @2.4x, remaining 12:47 RBU 100.0% UBU  99.7%
 2351267840/4699979776 (50.0%) @2.4x, remaining 12:43 RBU 100.0% UBU  99.7%
 2362114048/4699979776 (50.3%) @2.4x, remaining 12:39 RBU 100.0% UBU  99.7%
 2372993024/4699979776 (50.5%) @2.4x, remaining 12:36 RBU 100.0% UBU  99.7%
 2383806464/4699979776 (50.7%) @2.4x, remaining 12:32 RBU  99.6% UBU  99.7%
 2394619904/4699979776 (50.9%) @2.4x, remaining 12:28 RBU 100.0% UBU  99.7%
 2405466112/4699979776 (51.2%) @2.4x, remaining 12:24 RBU 100.0% UBU  99.7%
 2416345088/4699979776 (51.4%) @2.4x, remaining 12:20 RBU 100.0% UBU  99.7%
 2422112256/4699979776 (51.5%) @1.3x, remaining 12:20 RBU 100.0% UBU  99.7%
 2422243328/4699979776 (51.5%) @0.0x, remaining 12:23 RBU 100.0% UBU  11.9%
 2423455744/4699979776 (51.6%) @0.3x, remaining 12:25 RBU 100.0% UBU 100.0%
 2423455744/4699979776 (51.6%) @0.0x, remaining 12:28 RBU 100.0% UBU 100.0%
 2423455744/4699979776 (51.6%) @0.0x, remaining 12:32 RBU 100.0% UBU 100.0%
 2423455744/4699979776 (51.6%) @0.0x, remaining 12:35 RBU 100.0% UBU 100.0%
 2423455744/4699979776 (51.6%) @0.0x, remaining 12:38 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=120e60h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
:-( write failed: Input/output error
/dev/hdc: flushing cache
/dev/hdc: closing track
/dev/hdc: closing disc

growisofs command:
-----------------------
/usr/X11R6/bin/growisofs -Z /dev/hdc=/media/sda3/eduard/Bureaublad/wii.iso -use-the-force-luke=notray -use-the-force-luke=tty -dvd-compat -speed=1 -use-the-force-luke=bufsize:32m 

```

---

### Post by [flax] on 2007-12-15
On ubuntu i was stuborn and used the growisfs, i used the following command and again no result:

Should i burn the dvd slower? Maybe my system is to slow to burn under linux at the correct speed? :S

```

eduard@eduard-desktop:~$ growisofs -Z /dev/hdc=/home/eduard/Bureaublad/wii.iso -speed=0.5 -use-the-force-luke=bufsize:256m
Executing 'builtin_dd if=/home/eduard/Bureaublad/wii.iso of=/dev/hdc obs=32k seek=0'
/dev/hdc: "Current Write Speed" is 2.5x1352KBps.
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4699979776 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
    3964928/4699979776 ( 0.1%) @0.9x, remaining 927:46 RBU 100.0% UBU  70.4%
   13860864/4699979776 ( 0.3%) @2.1x, remaining 287:22 RBU 100.0% UBU  99.7%
:-[ WRITE@LBA=1a70h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
:-( write failed: Input/output error
/dev/hdc: flushing cache
/dev/hdc: closing track
/dev/hdc: closing session
/dev/hdc: reloading tray
eduard@eduard-desktop:~$ 

```

---

### Post by [flax] on 2007-12-15
Well, i now try to flash my liteon, but i can only download a exe. This exe, to flash the drive, does not work in wine or vmware (gives me an error about dma in guest operation system, after searching some forums it doesn thelp me much)
So, i placed my bet now on a tool, flash-X,  mentioned in a thread: [http://tweakers.net/meuktracker/5983/lite-on-ldw-811s-0q.html](http://tweakers.net/meuktracker/5983/lite-on-ldw-811s-0q.html) (i know, it is another type) which should be able to extract the data from an exectutable. 

Would flashing my drive help me, and if so, how can i do this? (and where can i find this tool "flash-X")

---

### Post by GreenMeanie on 2007-12-17
I also have a lite on giving me burning errors.
Keeps saying the media is bad when burning DVD's but yet it can burn a CD?

---

### Post by [flax] on 2007-12-18
GreenMeanie,
Do you have the same problems as me? (you can burn cd's but can't burn dvd's? under linux)  Can you tell me if you have the same device and what kind of error do you get and what are the steps you took before you got this error?

---

### Post by [flax] on 2007-12-21
I've removed the dvdplayer and put it into a windows machine, ran the firmware update and put it back into my machine. After this, the player didnt detect that it had a blank dvd anymore. Thus i sold the device and bought another dvd(a samsungsh-s202)

Too bad that i had to buy another device.

---

### Post by Sturmeh on 2008-04-26
You trying to burn Wii ISO's with ubuntu?

Sigh. :(

---

