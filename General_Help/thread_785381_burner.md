---
title: "burner"
date: 2008-05-07
forum: General Help
---

### Post by justborn on 2008-05-07
my default cd/dvd creator is not working & even the brasero burner.i cannot understand anything for the log.








please help me

---

### Post by spudratic on 2008-05-07
YOu really need to give more info.where does the problem occur.can the programs start do you get a bad burn.the stand alone dvd player can't read the disk.Do your best to describe the problem and some one will help.

---

### Post by justborn on 2008-05-07
the burner starts,the burning process also starts,but doesn't completeand i get an report of an unknown error 

now how can i explain an unknown error

---

### Post by bingoUV on 2008-05-07
> **justborn said:**
> my default cd/dvd creator is not working & even the brasero burner.i cannot understand anything for the log.



You said something about the log. Post the log here. Maybe someone here can figure something out.

---

### Post by justborn on 2008-05-07
the logis long
and simple 
cannot understand anay complications from it

---

### Post by justborn on 2008-05-07
[PHP]Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
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
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_input_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_add_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile finished track successfully
BraseroMd5sumFile stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
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
	/tmp/brasero_tmp_RSOTAU
	-exclude-list
	/tmp/brasero_tmp_2XOTAU
	-quiet
	-print-size
BraseroGenisoimage launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: HUP
BraseroGenisoimage stdout: 961
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_output_size_for_current_track
BraseroGenisoimage stdout: HUP
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
	dev=/dev/scd0
	gracetime=0
	speed=7
	driveropts=burnfree
	fs=4m
	tsize=961s
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
	/tmp/brasero_tmp_WQ33AU
	-exclude-list
	/tmp/brasero_tmp_AP33AU
	-V
	Data disc (07 May 08)
	-A
	Brasero-0.7.1
	-sysid
	LINUX
BraseroGenisoimage launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_input_type
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum starting md5 generation live
BraseroMd5sum called brasero_job_set_nonblocking
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum called brasero_job_get_fd_out
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum called brasero_job_get_fd_out
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/scd0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.6
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: SCSI buffer size: 64512
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: communication breaks or freezes immediately after that.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: TOC Type: 1 = CD-ROM
BraseroWodim stderr: Speed set to 1411 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Driveropts: 'burnfree'
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'TSSTcorp'
BraseroWodim stdout: Identification : 'CD-R/RW SH-R522C'
BraseroWodim stdout: Revision       : 'TS01'
BraseroWodim stdout: Device seems to be: Generic mmc CD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
BraseroWodim stdout: Drive buf size : 1016064 = 992 KB
BraseroWodim stdout: FIFO size      : 4194304 = 4096 KB
BraseroWodim stdout: Track 01: data     1 MB        
BraseroWodim stdout: Total size:        2 MB (00:12.81) = 961 sectors
BraseroWodim stdout: Lout start:        2 MB (00:14/61) = 961 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 5
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type B, low Beta category (B-) (4)
BraseroWodim stdout:   ATIP start of lead in:  -11834 (97:24/16)
BraseroWodim stdout:   ATIP start of lead out: 359849 (79:59/74)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 24
BraseroWodim stdout: Manufacturer: SONY Corporation
BraseroWodim stdout: Blocks total: 359849 Blocks current: 359849 Blocks remaining: 358888
BraseroWodim stdout: Starting to write CD/DVD at speed   8.0 in real SAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in  0 seconds. Operation starts.
BraseroWodim called brasero_job_set_dangerous
BraseroGenisoimage stderr: Total translation table size: 0
BraseroGenisoimage stderr: Total rockridge attributes bytes: 338
BraseroGenisoimage stderr: Total directory bytes: 0
BraseroGenisoimage stderr: Path table size(bytes): 10
BraseroGenisoimage stderr: Max brk space used 0
BraseroGenisoimage stderr: 961 extents written (1 MB)
BraseroGenisoimage stderr: HUP
BraseroGenisoimage process finished with status 0
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage finished track successfully
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroMd5sum
BraseroGenisoimage deactivating
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_input_type
BraseroMd5sum called brasero_job_get_current_track
BraseroMd5sum setting new checksum 81234b0e3b36f1aea0493f6c25ef658f (file:///tmp/brasero_tmp_UHUQAU.md5 before)
BraseroMd5sum finished track successfully
BraseroMd5sum disconnecting BraseroMd5sum from BraseroWodim
BraseroMd5sum closing connection for BraseroMd5sum
BraseroMd5sum deactivating
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stderr: Errno: 5 (Input/output error), send opc scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  54 01 00 00 00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:    3.762s
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: BURN-Free was never needed.
BraseroWodim stderr: Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: Sense Key: 0x3 Medium Error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 3.738s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: OPC failed.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo had 31 puts and 0 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: HUP
BraseroWodim process finished with status 255
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroWodim stopping
BraseroWodim got killed
BraseroWodim closing connection for BraseroWodim
Session error : unknown (brasero_burn_record burn.c:2273)
[/PHP]

---

### Post by mc4man on 2008-05-07
> BraseroWodim stdout: Performing OPC...
BraseroWodim stderr: Errno: 5 (Input/output error), send opc scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  54 01 00 00 00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:    3.762s
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: BURN-Free was never needed.
BraseroWodim stderr: Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: Sense Key: 0x3 Medium Error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 3.738s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: OPC failed. 

Your getting an opc error (optimum power calibration) Try using a different brand of media or google for drive specific info
here's the basics [http://www.fixya.com/support/t392500-power_calibration_error](http://www.fixya.com/support/t392500-power_calibration_error)

---

### Post by justborn on 2008-05-10
do u mean the drive does not support ma pc

---

### Post by bjbosch on 2008-05-11
Install K3B and try that. My Samsung burner does not work with Brasero. K3B at 8x works fine.

---

### Post by mc4man on 2008-05-13
> do u mean the drive does not support ma pc
no - more like your drive doesn't like your blank media

---

