---
title: "Problems burning cd's and dvd's"
date: 2008-05-10
forum: General Help
---

### Post by Maupertus on 2008-05-10
Since I upgraded to Hardy, I can't seem to burn any cd or dvd what so ever.

I've tried using Gnomebaker, Brasero and Nautilus, but each of these applications are giving me errors.

There are a couple of threads reporting different problems with either burning iso's or some other specific problems, but none of them get a solution and I think all these specific questions are actualy the same problem. So I wanted to make a more general thread that can hopefully help a couple of people (and me ofcourse :D)

This is the error I get with burning a cd, at the end it states that it probably has something to do with overburning, but in this 'test'-case, I explicitly burned some 500megs instead of the full 700 to see if that really was the problem and set the speed to 15.

[quote=Brasero]Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
BraseroMd5sumFile called brasero_job_get_output_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile deactivating
BraseroMd5sumFile called brasero_job_get_output_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_input_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_set_current_action
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_input_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_add_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile finished track successfully
BraseroMd5sumFile stopping
BraseroWodim called brasero_job_get_action
BraseroWodim creating input
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum creating input
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum deactivating
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage called brasero_job_start_progress
BraseroGenisoimage got varg:
	/usr/bin/genisoimage
	-input-charset
	utf8
	-r
	-J
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_H359AU
	-exclude-list
	/tmp/brasero_tmp_PY59AU
	-quiet
	-print-size
BraseroGenisoimage launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stdout: 288108
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_output_size_for_current_track
BraseroGenisoimage stdout: HUP
BraseroGenisoimage stderr: HUP
BraseroGenisoimage process finished with status 0
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage finished track successfully
BraseroGenisoimage got killed
BraseroGenisoimage stopping
BraseroWodim called brasero_job_get_action
BraseroWodim creating input
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_get_device
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_speed
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_session_output_size
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
	wodim
	-v
	dev=/dev/scd1
	gracetime=0
	speed=15
	driveropts=burnfree
	fs=25m
	tsize=288108s
	-dao
	-data
	-nopad
	-
BraseroWodim launching command
BraseroWodim called brasero_job_get_fd_out
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum linked to BraseroWodim
BraseroMd5sum creating input
BraseroMd5sum called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage linked to BraseroMd5sum
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_input_type
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum starting md5 generation live
BraseroMd5sum called brasero_job_set_nonblocking
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum called brasero_job_get_fd_out
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
	/usr/bin/genisoimage
	-input-charset
	utf8
	-r
	-J
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_XJ6BBU
	-exclude-list
	/tmp/brasero_tmp_78YBBU
	-V
	Data disc (10 May 08)
	-A
	Brasero-0.7.1
	-sysid
	LINUX
BraseroGenisoimage launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd1'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/scd1'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.6
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: SCSI buffer size: 64512
BraseroWodim called brasero_job_get_flags
BraseroGenisoimage stderr: Using CRYST000 for  C/Crystal Method (Crystal Castles)
BraseroGenisoimage stderr: Using COVER000.MP3;1 for  /media/sdb1/Music/C/Candlebox/Cover Me.mp3 (Cover Me (Acoustic).mp3)
BraseroWodim stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: communication breaks or freezes immediately after that.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: TOC Type: 1 = CD-ROM
BraseroWodim stdout: Driveropts: 'burnfree'
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'Optiarc '
BraseroWodim stdout: Identification : 'DVD RW AD-7173A '
BraseroWodim stdout: Revision       : '1-03'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0016 (DVD-R/DL layer jump recording) 
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0012 (DVD-RAM) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) (current)
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
BraseroWodim stdout: Drive buf size : 890880 = 870 KB
BraseroWodim stdout: FIFO size      : 26214400 = 25600 KB
BraseroWodim stderr: Speed set to 1411 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   562 MB        
BraseroWodim stdout: Total size:      646 MB (64:01.44) = 288108 sectors
BraseroWodim stdout: Lout start:      646 MB (64:03/33) = 288108 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 5
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type B, low Beta category (B-) (4)
BraseroWodim stdout:   ATIP start of lead in:  -11740 (97:25/35)
BraseroWodim stdout:   ATIP start of lead out: 359849 (79:59/74)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 40
BraseroWodim stdout: Manufacturer: INFODISC Technology Co., Ltd.
BraseroWodim stdout: Blocks total: 359849 Blocks current: 359849 Blocks remaining: 71741
BraseroWodim stdout: Starting to write CD/DVD at speed   8.0 in real SAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in  0 seconds. Operation starts.
BraseroWodim called brasero_job_set_dangerous
BraseroGenisoimage stderr: Using CANSE000 for  /media/sdb1/Music/C/CSS/Cansei de Ser Sexy (Disc 1) (Cansei de Ser Sexy)
BraseroGenisoimage stderr: Using CANSE001 for  /media/sdb1/Music/C/CSS/Cansei de Ser Sexy (Cansei De Ser Sexy)
BraseroGenisoimage stderr:   1.74% done, estimate finish Sat May 10 11:34:57 2008
BraseroGenisoimage called brasero_job_set_progress
BraseroGenisoimage called brasero_job_start_progress
BraseroGenisoimage stderr:   3.48% done, estimate finish Sat May 10 11:34:28 2008
BraseroGenisoimage called brasero_job_set_progress
BraseroGenisoimage called brasero_job_start_progress
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stdout: Sending CUE sheet...
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Writing pregap for track 1 at -150
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 00 01 93 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 04 00 00 00 00 0A 00 00 00 00 08 03 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x4 Hardware Error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.053s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 1
	message	= "a write error occured which was likely due to overburning the disc"
BraseroGenisoimage stopping
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroMd5sum
BraseroMd5sum stopping
BraseroMd5sum disconnecting BraseroMd5sum from BraseroWodim
BraseroMd5sum closing connection for BraseroMd5sum
BraseroWodim stopping
BraseroWodim got killed
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroWodim closing connection for BraseroWodim
Session error : a write error occured which was likely due to overburning the disc (brasero_burn_record burn.c:2270)
[/quote]

I hope someone can help me out.

---

### Post by adityakavoor on 2008-05-10
There is a bug reported in this regard

[https://bugs.launchpad.net/ubuntu/+bug/227886](https://bugs.launchpad.net/ubuntu/+bug/227886)

---

### Post by Maupertus on 2008-05-10
> **adityakavoor said:**
> There is a bug reported in this regard

[https://bugs.launchpad.net/ubuntu/+bug/227886](https://bugs.launchpad.net/ubuntu/+bug/227886)

Sorry, but this bug deals with slow burning and a high RAM/CPU use, the bugs I mentioned were in regard to no succes at burning at all.

---

### Post by adityakavoor on 2008-05-10
> **Maupertus said:**
> Sorry, but this bug deals with slow burning and a high RAM/CPU use, the bugs I mentioned were in regard to no succes at burning at all.

The person who reported the bug also hasn't successfully burnt a CD/DVD till date in Hardy

---

