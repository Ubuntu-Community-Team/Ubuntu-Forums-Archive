---
title: "Problem burning CDs"
date: 2007-05-14
forum: General Help
---

### Post by SteveF on 2007-05-14
I recently upgraded to Feisty from Edgy (I didn't have any problems with Edgy).  I have this same issue with both Kubuntu and Ubuntu.  My drive is accessible when I read from it.  When I put a CDRW in and use K3B, my CD drive becomes unusable.  K3B does not recognize a disk in the drive and from that point on, the drive is not usable.  I can't even read from it anymore (I have tried switching disks and nothing works) until I reboot.  Nothing recognizes the drive (or at least any disk in it) as being valid.  After rebooting, the drive is usable for reading until I try to write to it again.

I tried running cdrecord at the command prompt.  It mentioned something about setting CDR_NODMATEST if the drive freezes and then proceeds to freeze the drive.  So I reboot.  I set the env variable.  But I still get the same problem.

I've tried using cdrecord as regular user and using sudo (which I did not have to do in Edgy).  But both freeze the drive up.

Has anyone else had similar problems?  Is there something I can check to free the drive up and get it working again?

Thanks,

Steve

---

### Post by SteveF on 2007-05-14
Looks like it might just be bad luck.  I booted into Windows so I could back up my files.  First disk went without problems (after which I had posted the original message assuming it was a Feisty issue).  During the second disk burn, it locked up the drive just like Linux.  So it appears I may have faulty hardware (just timed perfectly with my first Feisty burn).

Steve

---

### Post by SteveF on 2007-05-14
I'm going to change my mind on my last post.  I'm not convinced its the cd burner.  I tried a different cdrw in Windows and it worked fine.  I tried using different ones in Kubuntu. The first time I called cdrecord from the command prompt and the erase worked.  I then went into K3B.  It burned the CD but then failed when verifying (it could not get the drive anymore - occurred after drive opened and closed).

After that, the drive was unusable again.

The fact Windows only failed on the one disk and other disks are working makes me think it is a Feisty issue.  I'm really thinking the problem is with something in Feisty that is not handling the CD drive correctly.  I'm not ready to go out an spend money on a potentially unneeded cd drive (especially since I see notes showing problems with burning under feisty).

When did K/Ubuntu start using wodim in place of cdrecord?

Has anyone seen problems like this before?

Steve

---

### Post by firstcupoffreshpressed on 2007-05-14
I discovered my first problem in feisty trying to burn a cd.  I spent hours researching the forums and found others who have  had an identical or similar problem.  None of the solutions appeared to work for me.  Finally I clean installed Dapper because I gave my beautiful feisty cd to a friend.  I'm able to burn again with Dapper.

One of the suggestions I tried was using Brasero to burn cd's.  After reinstalling Dapper I discovered that Brasero had put a file the right size on one of the cd's I was using to try to burn.  I don't know if its a usable data cd yet. .  This was a trial for me because I am a newb with 4 months experience.

I nearly changed to Debian and want to see a fix for this before I use feisty.   Although I will probably try installing again on another drive to see if this was an instll glitch or some evil bug.

---

### Post by SteveF on 2007-05-14
> **firstcupoffreshpressed said:**
> I discovered my first problem in feisty trying to burn a cd.  I spent hours researching the forums and found others who have  had an identical or similar problem.  None of the solutions appeared to work for me.  Finally I clean installed Dapper because I gave my beautiful feisty cd to a friend.  I'm able to burn again with Dapper.

One of the suggestions I tried was using Brasero to burn cd's.  After reinstalling Dapper I discovered that Brasero had put a file the right size on one of the cd's I was using to try to burn.  I don't know if its a usable data cd yet. .  This was a trial for me because I am a newb with 4 months experience.

I nearly changed to Debian and want to see a fix for this before I use feisty.   Although I will probably try installing again on another drive to see if this was an instll glitch or some evil bug.

Thanks for the reply.  After burning and erasing 3 more disks with Windows and not getting Feisty to use the drive more than once as a burner, I really believe it is a Feisty issue and I think it is related to how Fesity represents the burner as a SCSI drive now (even though it is an internal IDE drive).

I tried downloading cdrecord source and compiling it (in case wodim was to blame).  It can't handle the SCSI designation of the burner and won't work.

I may have to reinstall Edgy (I just don't look forward to the work, but I need to be able to burns CDs).

Steve

---

### Post by firstcupoffreshpressed on 2007-05-15
that's the kind of idea I got also.  sda, hda confusion

The brasero app  may have worked.  I have burned a new feisty cd and am going to try a new install.  I still haven't checked the cd dapper says has the feisty brasero data burn on it. [windows software for another machine]

Everyone is not having this issue [evidently] and sometimes my dapper and debian installs had problems solved by a fresh install. 

From what I have read in forum some people having this problem have found a working solution with feisty.

---

### Post by SteveF on 2007-05-16
> **firstcupoffreshpressed said:**
> that's the kind of idea I got also.  sda, hda confusion

The brasero app  may have worked.  I have burned a new feisty cd and am going to try a new install.  I still haven't checked the cd dapper says has the feisty brasero data burn on it. [windows software for another machine]

Everyone is not having this issue [evidently] and sometimes my dapper and debian installs had problems solved by a fresh install. 

From what I have read in forum some people having this problem have found a working solution with feisty.

I decided to bite the bullet and do a fresh install of Feisty.  After doing that, I was able not able to burn a CD with K3B.  It acted like it burned, but there was nothing on the disk.  Then the drive was unusable.  I then tried burning form the command line.  I was able to erase the CDRW and do one burn.  The burn worked, but after that, the drive was unusable again.

I repeated the same tests, but instead installed a fresh Edgy over my other distribution.  I had a similar problem in K3B.  It would burn, but nothing was there.  But at least I didn't lose the drive this time.  So I tried to burn from command line.  So far that seems to have worked.  I'm not sure what is going on with K3B.

All test have been on CDRWs.  I'm going to try a plain CDR and see how it works (after I reboot).

Steve

---

### Post by kelvin spratt on 2007-05-16
I use Fiesty have burned 100+ CDRW discs and DVDs, i do not use k3b i use Brasero and Nero
and both give excellent results

---

### Post by SteveF on 2007-05-16
> **kelvin spratt said:**
> I use Fiesty have burned 100+ CDRW discs and DVDs, i do not use k3b i use Brasero and Nero
and both give excellent results

I'll take a look at Brasero.  
I was able to burn to burn a CDR.  So now I'm wondering if it is related to unmounting a cdrw prior to use.

Steve

---

### Post by bierholen on 2007-05-23
I recently switched from openSUSE 10.2 to Kubuntu 7.04 Feisty. Pretty much everything is working fine except for one thing: I can't burn anything any more and it's driving me nuts. I wasted more than 20 recordable CDs and DVDs so far. 

I don't have the best CD/DVD burner in my laptop but I use well chosen brand name media and they worked mostly well under openSUSE 10.2 so this simply can't be right. I tried K3b, GnomeBaker, Xcdroast, Nero, and Brasero (see error messages below). I also think that it has to do with this SCSI vs. IDE thing. I clearly have an IDE optical drive and that's how it was handled under openSUSE where everything was fine. I installed Feisty on another 5 year old laptop as well. Surprisingly, burning CDs with K3b worked great. No problems at all. I checked and it was mounted as /dev/hdc so handled as IDE drive. Another hint that makes me believe that there is something wrong with the way Feisty deals with the burner in my newer laptop. I wonder what makes Feisty decide to chose SCSI or IDE... This issue has been discussed in many threads, e.g.:

[http://ubuntuforums.org/showthread.php?t=415057&highlight=hdparm]("http://ubuntuforums.org/showthread.php?t=415057&highlight=hdparm")
[http://ubuntuforums.org/showthread.php?t=405630&highlight=HDIO_SET_DMA+failed%3A+Inappropriate+ioctl+for+device]("http://ubuntuforums.org/showthread.php?t=405630&highlight=HDIO_SET_DMA+failed%3A+Inappropriate+ioctl+for+device")

Is this a bug, would a new kernel fix this? By the way someone suggested to do the following in the second thread above:

$ sudo modprobe sr_mod
$ sudo modprobe cdrom
$ dmesg | tail

I get the following output:

[16363.388000] TKIP: ICV error detected: STA=00:15:e9:1d:3c:22
[16385.140000] TKIP: ICV error detected: STA=00:15:e9:1d:3c:22
[16385.912000] TKIP: ICV error detected: STA=00:15:e9:1d:3c:22
[16419.600000] TKIP: ICV error detected: STA=00:15:e9:1d:3c:22
[16420.012000] TKIP: ICV error detected: STA=00:15:e9:1d:3c:22
[16436.744000] TKIP: ICV error detected: STA=00:15:e9:1d:3c:22
[16437.620000] TKIP: ICV error detected: STA=00:15:e9:1d:3c:22
[16447.860000] TKIP: ICV error detected: STA=00:15:e9:1d:3c:22
[16577.124000] TKIP: ICV error detected: STA=00:15:e9:1d:3c:22
[16577.388000] TKIP: ICV error detected: STA=00:15:e9:1d:3c:22


I really don't know what that means but it doesn't look good...Does anyone have any ideas?

______________________________________________________________________________

Error outputs:

[HTML]
K3b 1.0: CD-R

System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-15-generic
Devices
-----------------------
QSI DVD+-RW SDW-082 LX51 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R16, RAW/R96R, Restricted Overwrite]

K3bIsoImager
-----------------------
mkisofs print size result: 357483 (732125184 bytes)
Pipe throughput: 276400896 bytes read, 276396544 bytes written.

Used versions
-----------------------
mkisofs: 1.1.2
cdrecord: 1.1.2

cdrecord
-----------------------
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'QSI     '
Identification : 'DVD+-RW SDW-082 '
Revision       : 'LX51'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0000 (Reserved/Unknown) 
Profile: 0x0000 (Reserved/Unknown) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1073152 = 1048 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 2822 KB/s
Track 01: data   698 MB        
Total size:      801 MB (79:26.44) = 357483 sectors
Lout start:      802 MB (79:28/33) = 357483 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 2363
Starting to write CD/DVD at speed  16.0 in real SAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Errno: 5 (Input/output error), read track info scsi sendcmd: no error
CDB:  52 01 00 00 00 FF 00 00 1C 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 28
cmd finished after 0.002s timeout 240s
/usr/bin/wodim: Cannot get next writable address for 'invisible' track.
/usr/bin/wodim: This means that we are checking recorded media.
/usr/bin/wodim: This media cannot be written in streaming mode anymore.
/usr/bin/wodim: If you like to write to 'preformatted' RW media, try to blank the media first.
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  698 MB written.
Track 01:    1 of  698 MB written (fifo 100%) [buf  87%]   3.7x.

[...]

Track 01:  251 of  698 MB written (fifo  99%) [buf  84%]  11.3x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 01 F7 DF 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 37.540s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 264173568 bytes
Writing  time:  215.654s
Average write speed  22.1x.
Min drive buffer fill was 63%
Fixating...
Fixating time:    0.007s


GnomeBaker 0.6: CD-R

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'QSI     '
Identification : 'DVD+-RW SDW-082 '
Revision       : 'LX51'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1073152 = 1048 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 2822 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 01 77 83 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 47 00 00 00 00 0E 09 0C 00 00 00 01 00 00
Sense Key: 0x7 Data Protect, Segment 11
Sense Code: 0x00 Qual 0x01 (filemark detected) Fru 0x0
Sense flags: Blk 0 (not valid) end of medium 
resid: 63488
cmd finished after 0.639s timeout 40s
wodim: A write error occured.
wodim: Please properly read the error message above.

write track data: error after 196876288 bytes
Writing  time:  149.320s
Average write speed  31.9x.
Min drive buffer fill was 87%
Fixating...
Fixating time:   37.929s


Brassero Brasero 0.5.2: DVD-R

imager (BraseroLocalImage) set_output
job (BraseroLocalImage) set_task
imager (BraseroLocalImage) get_track
job (BraseroLocalImage) set_task
Session starting:
	flags			= 16727 
	media type	= 0
	speed		= 3
	track type		= 8
	track format	= 2
	output		= none
job (BraseroGrowisofs) set_rate
recorder (BraseroGrowisofs) set_drive
recorder (BraseroGrowisofs) set_flags
job (BraseroGrowisofs) set_source
job (BraseroGrowisofs) set_task
recorder (BraseroGrowisofs) record
process (BraseroGrowisofs) getting varg
growisofs (BraseroGrowisofs) set_action
process (BraseroGrowisofs) got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-speed=3
	-dvd-compat
	-use-the-force-luke=tty
	-Z
	/dev/scd0=/*/*.iso
process (BraseroGrowisofs) launching command
process (BraseroGrowisofs) stdout: Executing 'builtin_dd if=/*/*.iso of=/dev/scd0 obs=32k seek=0'
process (BraseroGrowisofs) stderr: /dev/scd0: engaging DVD-R DAO upon user request...
process (BraseroGrowisofs) stderr: /dev/scd0: reserving 1135069 blocks
process (BraseroGrowisofs) stderr: /dev/scd0: "Current Write Speed" is 4.1x1352KBps.
process (BraseroGrowisofs) stdout:           0/2324621312 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
process (BraseroGrowisofs) stdout:           0/2324621312 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
process (BraseroGrowisofs) stdout:           0/2324621312 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
process (BraseroGrowisofs) stdout:           0/2324621312 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
process (BraseroGrowisofs) stdout:           0/2324621312 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
process (BraseroGrowisofs) stdout:           0/2324621312 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
process (BraseroGrowisofs) stdout:           0/2324621312 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
process (BraseroGrowisofs) stdout:           0/2324621312 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
process (BraseroGrowisofs) stdout:      655360/2324621312 ( 0.0%) @0.1x, remaining 1950:20 RBU 100.0% UBU   4.8%
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_rate
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stdout:      655360/2324621312 ( 0.0%) @0.0x, remaining 2127:39 RBU 100.0% UBU 100.0%
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_rate
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress

[...]

process (BraseroGrowisofs) stdout:   638844928/2324621312 (27.5%) @0.0x, remaining 12:03 RBU 100.0% UBU 100.0%
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_rate
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr: :-[ WRITE@LBA=4cca0h failed with SK=7h/ASC=00h/ACQ=01h]: Input/output error
process (BraseroGrowisofs) stderr: :-( write failed: Input/output error
job (BraseroGrowisofs) asked to stop
	status	= 1
	error		= 1
	message	= "Unhandled error, aborting"
iter (BraseroGrowisofs) stopping
process (BraseroGrowisofs) got killed
iter (BraseroGrowisofs) stopped
job (BraseroGrowisofs) got out of loop
job (BraseroGrowisofs) set_task
Session error : Unhandled error, aborting

[...]

Nero 3.0.0.0 beta: DVD-R

Linux 2.6.20-15-generic
Nero API version: 7.5.14.2
Using interface version: 7.5.0.2
Installed in: /usr/lib/nero/
Application: Nero AG\Nero Linux
Internal Version: 7, 5, 14, 2

Recorder:             <QSI DVD+-RW SDW-082>     Version: LX51 - HA 1 TA 0 - 0.0.0.0
 Adapter driver:      <ata_piix>                HA 1
 Drive buffer  :      2048kB
 Bus Type      :      default (0) -> SCSI, detected: ?
Excluded drive IDs: 
WriteBufferSize: 83886080 (0) Byte
BUFE           : 0
Physical memory     : 1248MB (1278524kB)
Free physical memory: 104MB (107404kB)
Memory in use       : 91 %
Uncached PFiles: 0x0
Use Inquiry    : 1
Global Bus Type: default (0)
Check supported media : Disabled (0) 

22.5.2007
NeroAPI
08:23:51 PM	#1 Text 0 File Burncd.cpp, Line 3490
	Turn on Disc-At-Once, using DVD media
	
08:23:52 PM	#2 Text 0 File DlgWaitCD.cpp, Line 307
	Last possible write address on media:  2298495 (510:46.45, 4489MB)
	Last address to be written:            1135068 (252:14.18, 2216MB)
	
08:23:52 PM	#3 Text 0 File DlgWaitCD.cpp, Line 319
	Write in overburning mode: NO
	
08:23:52 PM	#4 Text 0 File DlgWaitCD.cpp, Line 2951
	Recorder: QSI DVD+-RW SDW-082, Media type: DVD-R
	 Disc Manufacturer: RITEKF - 1
	 Disc Application Code: 64, Disc Physical Code: 193
	
08:23:52 PM	#5 Text 0 File DlgWaitCD.cpp, Line 493
	>>> Protocol of DlgWaitCD activities: <<<
	=========================================
	
08:23:52 PM	#6 Text 0 File ThreadedTransferInterface.cpp, Line 792
	Setup items (after recorder preparation)
	 0: TRM_DATA_MODE1 (2 - CD-ROM Mode 1, ISO 9660)
	    2 indices, index0 (150) not provided
	    original disc pos #0 + 1135069 (1135069) = #1135069/252:14.19
	    not relocatable, disc pos for caching/writing not required/not required
	    -> TRM_DATA_MODE1, 2048, config 0, wanted index0 0 blocks, length 1135069 blocks [QSI DVD+-RW SDW-082 (H:1 T:0)]
	--------------------------------------------------------------
	
08:23:52 PM	#7 Text 0 File ThreadedTransferInterface.cpp, Line 995
	Prepare [QSI DVD+-RW SDW-082 (H:1 T:0)] for write in CUE-sheet-DAO
	DAO infos:
	==========
	 MCN: ""
	 TOCType: 0x00; Session Closed, disc fixated
	 Tracks 1 to 1:                                  Idx 0         Idx 1      Next Trk
	   1: TRM_DATA_MODE1, 2048/0x00, FilePos             0             0    2324621312, ISRC ""
	DAO layout:
	===========
	 ___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
	        0 |  lead-in |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   1 |    0x41 |  1135069 |  1135069 | 0x00
	  1135069 | lead-out |   1 |    0x41 |        0 |        0 | 0x00
	
08:23:52 PM	#8 Text 0 File Burncd.cpp, Line 4263
	Caching options: cache CDRom or Network-No, small files-Yes (<32KB)
	
08:23:52 PM	#9 Phase 24 File ExtendedProgress.cpp, Line 537
	Caching of files started
	
08:23:52 PM	#10 Text 0 File Burncd.cpp, Line 4382
	Cache writing successful.
	
08:23:52 PM	#11 Phase 25 File ExtendedProgress.cpp, Line 537
	Caching of files completed
	
08:23:52 PM	#12 Phase 36 File ExtendedProgress.cpp, Line 537
	Burn process started at 4x (5540 KB/s)
	
08:23:52 PM	#13 Text 0 File ThreadedTransferInterface.cpp, Line 2712
	Verifying disc position of item 0 (not relocatable, no disc pos, no patch infos, orig at #0): write at #0
	
08:23:52 PM	#14 Text 0 File DVDR.cpp, Line 3151
	Recording mode: Sequential Recording Mode
	
08:23:52 PM	#15 Text 0 File DVDR.cpp, Line 3307
	Start write address at LBA 0
	DVD high compatibility mode: Yes
	
08:23:52 PM	#16 Text 0 File Cdrdrv.cpp, Line 9885
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
	
08:23:52 PM	#17 Text 0 File ThreadedTransfer.cpp, Line 269
	Pipe memory size 83836800
	
08:23:53 PM	#18 Text 0 File Cdrdrv.cpp, Line 1347
	20:23:53 - QSI DVD+-RW SDW-082 (H:1 T:0) : Queue again later
	
08:32:13 PM	#19 SCSI -400 File SCSIInterface.cpp, Line 622
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xaee0bc40
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x02 (0x01, SCSI_TASTATUS_CHKCOND)
	Sense Key:  0x07 (Unknown)
	Sense Code: 0x00
	Sense Qual: 0x01
	CDB Data:   0x2A 0x00 0x00 0x0E 0xC8 0x40 0x00 0x00 0x20 0x00 
	Sense Data: 0x72 0x0B 0x47 0x00 0x00 0x00 0x00 0x0E 
	            0x09 0x0C 0x00 0x00 0x00 0x01 
	
08:32:13 PM	#20 CDR -400 File Writer.cpp, Line 299
	Unspecified target error
	QSI DVD+-RW SDW-082 (H:1 T:0)
	
08:32:13 PM	#21 Text 0 File DVDR.cpp, Line 3709
	EndDAO: Last written address was 968767 (EC83Fh)
	
08:32:14 PM	#22 Phase 38 File ExtendedProgress.cpp, Line 537
	Burn process failed at 4x (5540 KB/s)


xcdroast 0.98alpha15: DVD-R

Calling: /usr/lib/xcdroast/bin/xcdrwrap CDRECORDDVD dev= "1,0,0" gracetime=10 fs=4096k driveropts=burnfree -v -useinfo speed=4 -dao -eject -pad -data "/*/*.iso" ...

scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
TOC Type: 1 = CD-ROM
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
Driveropts: 'burnfree'
communication breaks or freezes immediately after that.
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   :
Vendor_info    : 'QSI     '
Identification : 'DVD+-RW SDW-082 '
Revision       : 'LX51'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0011 (DVD-R sequential recording)
Profile: 0x002B (DVD+R/DL)
Profile: 0x001B (DVD+R)
Profile: 0x001A (DVD+RW)
Profile: 0x0014 (DVD-RW sequential recording)
Profile: 0x0013 (DVD-RW restricted overwrite)
Profile: 0x0011 (DVD-R sequential recording) (current)
Profile: 0x0010 (DVD-ROM)
Profile: 0x000A (CD-RW)
Profile: 0x0009 (CD-R)
Profile: 0x0008 (CD-ROM)
Profile: 0x0000 (Reserved/Unknown)
Profile: 0x0000 (Reserved/Unknown)
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE
Supported modes: PACKET SAO
Drive buf size : 688128 = 672 KB
Speed set to 5540 KB/s
FIFO size      : 4194304 = 4096 KB
Track 01: data  2216 MB         padsize:   30 KB
Total size:     2546 MB (252:14.45) = 1135084 sectors
Lout start:     2546 MB (252:16/34) = 1135084 sectors
Current Secsize: 2048
ATIP start of lead in:  -150 (00:00/00)
Disk type:    unknown dye (reserved id code)
Manuf. index: -1
Manufacturer: unknown (not in table)
Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 1163412
Starting to write CD/DVD at speed   4.0 in real SAO mode for single session.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Starting new track at sector: 0
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 06 1B 52 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 47 00 00 00 00 0E 09 0C 00 00 00 01 00 00
Sense Key: 0x7 Data Protect, Segment 11
Sense Code: 0x00 Qual 0x01 (filemark detected) Fru 0x0
Sense flags: Blk 0 (not valid) end of medium 
resid: 63488
cmd finished after 0.638s timeout 200s
wodim: A write error occured.
wodim: Please properly read the error message above.

write track data: error after 819630080 bytes
Writing  time:  286.124s
Average write speed   5.9x.
Min drive buffer fill was 47%
Fixating...
Fixating time:    2.485s
[/HTML]

---

### Post by andrew.46 on 2007-05-23
Hi,

 I have a deep suspicion that Feisty has some issues with CD and DVD burning. I had a rolling series of problems with Feisty and a growing pile of frisbees before I downgraded to Dapper. Under Dapper CD burning and DVD burning is flawless.Filed a bug report that has not been looked at yet.

                   Andrew

---

### Post by stchman on 2007-05-25
> **SteveF said:**
> I recently upgraded to Feisty from Edgy (I didn't have any problems with Edgy).  I have this same issue with both Kubuntu and Ubuntu.  My drive is accessible when I read from it.  When I put a CDRW in and use K3B, my CD drive becomes unusable.  K3B does not recognize a disk in the drive and from that point on, the drive is not usable.  I can't even read from it anymore (I have tried switching disks and nothing works) until I reboot.  Nothing recognizes the drive (or at least any disk in it) as being valid.  After rebooting, the drive is usable for reading until I try to write to it again.

I tried running cdrecord at the command prompt.  It mentioned something about setting CDR_NODMATEST if the drive freezes and then proceeds to freeze the drive.  So I reboot.  I set the env variable.  But I still get the same problem.

I've tried using cdrecord as regular user and using sudo (which I did not have to do in Edgy).  But both freeze the drive up.

Has anyone else had similar problems?  Is there something I can check to free the drive up and get it working again?

Thanks,

Steve

I have burned multiple CDs using K3B on Feisty and no problems.

---

### Post by divali on 2007-05-29
Yes, I'm having the same problem and I'm using Feisty too.  I've tried Serpentine, K3b and Gnome Baker and got this message:

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... giving up.
TOC Type: 0 = CD-DA
scsidev: 'ATA:/dev/hdd'
devname: 'ATA:/dev/hdd'
scsibus: -2 target: -2 lun: -2
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

I'm not sure what it all means.

In the meantime I will use Knoppix to burn my cd's, at least, until we resolve this problem.

---

### Post by zodmaner on 2007-05-29
Try disable DMA using this command:

>  sudo hdparm -d0 -k1 /dev/cdrom 

and set the burn speed to as low as possible. I have similar problem and disable DMA help solve my problem.

---

### Post by divali on 2007-05-29
Hmmm.     Thanks, I just saw your discussion with Pragmatist. I'll give it a wizz and let you know
how I get on.

---

### Post by divali on 2007-05-29
Quote:   sudo hdparm -d0 -k1 /dev/cdrom

Thanks, that solved my problem of cd's that wont burn using K3b. It took me all day trying to solve 
the problem.  It does slow the process down a lot but, what the heck. I also think it's necessary to reboot afterwards. 
I'll try to re-enable DMA once this is sorted out. It seems to be caused by an update, judging by the 
comments on the forum.

---

### Post by stchman on 2007-05-29
> **SteveF said:**
> I recently upgraded to Feisty from Edgy (I didn't have any problems with Edgy).  I have this same issue with both Kubuntu and Ubuntu.  My drive is accessible when I read from it.  When I put a CDRW in and use K3B, my CD drive becomes unusable.  K3B does not recognize a disk in the drive and from that point on, the drive is not usable.  I can't even read from it anymore (I have tried switching disks and nothing works) until I reboot.  Nothing recognizes the drive (or at least any disk in it) as being valid.  After rebooting, the drive is usable for reading until I try to write to it again.

I tried running cdrecord at the command prompt.  It mentioned something about setting CDR_NODMATEST if the drive freezes and then proceeds to freeze the drive.  So I reboot.  I set the env variable.  But I still get the same problem.

I've tried using cdrecord as regular user and using sudo (which I did not have to do in Edgy).  But both freeze the drive up.

Has anyone else had similar problems?  Is there something I can check to free the drive up and get it working again?

Thanks,

Steve

Did you do a fresh install of Feisty?  I tried the upgrade path and a lot of stuff did not work properly.  I then did a clean install and all was well.  I recommend a clean install and use my script:

[http://www.stchman.com/feisty_script.html](http://www.stchman.com/feisty_script.html)

This will install a lot of the popular applications.  I have used this script on many different machines and it works awesome.  It will enable mp3, DVD decryption, K3b.

I installed Feisty on a machine, used the restricted drivers, and used my script all in under an hour.

Hope this helps.

---

### Post by bierholen on 2007-05-29
My problem seems to be solved. A kernel update from 2.6.20-15 to 2.6.20-16 changed the burner from /dev/scd0 to /dev/hdc and ever since I can burn again (at least so far).

---

### Post by SteveF on 2007-05-30
Well, my original problem seems to be solved (more testing needed).  The new kernel that was just installed seems to have solved the problem.

Steve

---

### Post by SteveF on 2007-05-30
> **SteveF said:**
> Well, my original problem seems to be solved (more testing needed).  The new kernel that was just installed seems to have solved the problem.

Steve

I've burnt another disk without problems, so it looks like the issue may be fixed.

I did notice that the device changed back to /dev/hdc from /dev/sdc0.  This may be the reason it works now (I did have to modify my fstab and scripts which referenced scd0).  I'm thinking CD and SCSI device were not mixing well.

Steve

---

### Post by SteveF on 2007-06-20
Well it looks like the latest update switched the cdrom drive back to /dev/scd0 instead of using /dev/hdc and now my CD drive is broken again.

Anyone else back to having problems?

Steve

---

### Post by bierholen on 2007-06-26
Yepp, exactly the same here. Sucks.

---

### Post by UK-Wobbie on 2007-06-26
> **SteveF said:**
> I recently upgraded to Feisty from Edgy (I didn't have any problems with Edgy).  I have this same issue with both Kubuntu and Ubuntu.  My drive is accessible when I read from it.  When I put a CDRW in and use K3B, my CD drive becomes unusable.  K3B does not recognize a disk in the drive and from that point on, the drive is not usable.  I can't even read from it anymore (I have tried switching disks and nothing works) until I reboot.  Nothing recognizes the drive (or at least any disk in it) as being valid.  After rebooting, the drive is usable for reading until I try to write to it again.

I tried running cdrecord at the command prompt.  It mentioned something about setting CDR_NODMATEST if the drive freezes and then proceeds to freeze the drive.  So I reboot.  I set the env variable.  But I still get the same problem.

I've tried using cdrecord as regular user and using sudo (which I did not have to do in Edgy).  But both freeze the drive up.

Has anyone else had similar problems?  Is there something I can check to free the drive up and get it working again?

Thanks,

Steve

It may be the cd drive ubuntu do not like! Ubuntu and kubuntu are the same so it may be that!
I have got a cd drive what i use to use on ubuntu what was only a cd and cd r burnner! When i copy music cds it use to crash when it gets to the burning. So it may be that ubuntu have not got the right pluggings for it or it do not like it :)

---

### Post by SteveF on 2007-06-27
> **UK-Wobbie said:**
> It may be the cd drive ubuntu do not like! Ubuntu and kubuntu are the same so it may be that!
I have got a cd drive what i use to use on ubuntu what was only a cd and cd r burnner! When i copy music cds it use to crash when it gets to the burning. So it may be that ubuntu have not got the right pluggings for it or it do not like it :)

Though that is possible, I'm thinking it may not be true because the drive worked fine starting from Hoary to Breezy to Dapper to Edgy.  Only Feisty has had a problem.  Also, when Feisty temporarily used hdc as the device instead of scd0, it did work.

So I think it is related to the SCSI naming convention now used.

I'm playing around with cdrskin as an alternative to using cdrecord/wodim.  Burning actually worked once (won't blank the cdrw though).  So with partial success I may download and compile the newer version.

Steve

---

### Post by bierholen on 2007-06-27
I agree with SteveF, With respect to Feisty, I observed the following:

1. Kernel 2.6.20-15: /dev/scd0 > burner couldn't burn anything

2. Kernel 2.6.20-16.28: /dev/hdc > burner was fine

3. Kernel 2.6.20-16.29: /dev/scd0 > burner can't burn anything any more


I installed edgy the other day and had no problems with the burner.

---

### Post by kelvin spratt on 2007-06-27
Never had a problem i burn 10 - 15 times a day with Feisty use verbatim and my Plextor writer premium gear all the way,

---

### Post by SteveF on 2007-06-27
> **bierholen said:**
> I agree with SteveF, With respect to Feisty, I observed the following:

1. Kernel 2.6.20-15: /dev/scd0 > burner couldn't burn anything

2. Kernel 2.6.20-16.28: /dev/hdc > burner was fine

3. Kernel 2.6.20-16.29: /dev/scd0 > burner can't burn anything any more


I installed edgy the other day and had no problems with the burner.

In case you're interested, I started another thread to see if what I did was OK with the system.  The title got messed up, but search on SteveF in advanced search.  The title contains initrd in it (too many times by accident).  I was able to revert to 2.6.20-16.28 (at least I hope I did it right).  Might work for you.

Steve

---

### Post by Juicespeare1 on 2007-06-28
Hmm, I posted a new post today as I'm having the same issues. The CD drive is also listed as /dev/scd0.

This is a fresh install of Ubuntu Feisty 7.04. This machine had no OS prior to this installation.

BR
Juicespeare1



Here's my post:
====================

 Strange issues trying to burn CD's in Ubuntu Feisty 7.04
Hi all,

Just joined the forum. This is my second post.

I've been using Ubuntu for a couple of months.

On one of my machines an IBM Netvista I'm having issues trying to burn CD's.

IBM hardware more info here [http://www-307.ibm.com/pc/support/si...IGR-39334.html](http://www-307.ibm.com/pc/support/si...IGR-39334.html)

The issues are:

1.) I can't burn any CD, CD-R or CD-RW, nothing works. The actual burn process fails and doesn't even try to burn the CD at the beginning of the write state.

The burn process always fails (I've tried a couple of burning applications and all fail). Prior to trying to burn a CD, the CD burner can read CD's. After trying to burn a CD, the CD drive stops working completely (can't eject or read CD's or anything) until a shutdown, see below.

2.) After the burn fails I cannot eject a CD, cannot umount CD, cannot mount CD, can't even manually open the CD drive's drawer by pressing the open button on the CD drive. I have to shutdown the PC in order for the CD drive to be accessible again.

Logging out and reboot doesn't even work, only a physical power down works. I've even tried to eject the CD with a paperclip and still the drive is inaccessible until a shutdown is performed.

This CD burner works fine in another PC and also works fine in an external enclosure on another PC. The CD's I put in the burner are readable in Ubuntu prior to a burn attempt, but after a burn attempt, the CD drive is totally hosed up as far as CD recognition goes. The CD drive completely stops working until a shutdown is performed.

Any ideas?

BTW - the CD burner is a Cyberdrive 32x burner.

I can provide logs if someone can tell me where to get them, or even screen captures if need be.

BTW - I'm using Ubuntu Feisty 7.04 desktop edition.

BR
Juicespeare1

---

