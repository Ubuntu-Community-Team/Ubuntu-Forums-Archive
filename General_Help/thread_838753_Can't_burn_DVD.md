---
title: "Can't burn DVD"
date: 2008-06-23
forum: General Help
---

### Post by muzikoverdose on 2008-06-23
I'm trying to backup some avi's to DVD for storage. I've tried both Brasero and the default burning program and each time i get an error. Im running 8.04 on a Fujitsu Lifebook 3210.  it seems to read DVD's and from from them fine.  Any help would be greatly appreciated.  

the Brasero error log is as follows:

Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
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
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_input_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_add_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile finished track successfully
BraseroMd5sumFile stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-speed=8
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-dry-run
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_XJ5BDU
	-exclude-list
	/tmp/brasero_tmp_0VHDDU
	-print-size
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -D -path-list /tmp/brasero_tmp_XJ5BDU -exclude-list /tmp/brasero_tmp_0VHDDU -print-size | builtin_dd of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous

BraseroGrowisofs stderr: Total extents scheduled to be written = 1970490
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_output_size_for_current_track
BraseroGrowisofs finished successfully session
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_data_label
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-speed=8
	-use-the-force-luke=tracksize:1970490
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_243LDU
	-exclude-list
	/tmp/brasero_tmp_623LDU
	-V
	Backup
	-A
	Brasero-0.7.1
	-sysid
	LINUX
	-v
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stderr: genisoimage 1.1.6 (Linux)
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -D -path-list /tmp/brasero_tmp_243LDU -exclude-list /tmp/brasero_tmp_623LDU -V Backup -A Brasero-0.7.1 -sysid LINUX -v | builtin_dd of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous

BraseroGrowisofs stderr: Writing:   Initial Padblock                        Start Block 0
BraseroGrowisofs stderr: Done with: Initial Padblock                        Block(s)    16
BraseroGrowisofs stderr: Writing:   Primary Volume Descriptor               Start Block 16
BraseroGrowisofs stderr: Done with: Primary Volume Descriptor               Block(s)    1
BraseroGrowisofs stderr: Writing:   Joliet Volume Descriptor                Start Block 17
BraseroGrowisofs stderr: Done with: Joliet Volume Descriptor                Block(s)    1
BraseroGrowisofs stderr: Writing:   End Volume Descriptor                   Start Block 18
BraseroGrowisofs stderr: Done with: End Volume Descriptor                   Block(s)    1
BraseroGrowisofs stderr: Writing:   Version block                           Start Block 19
BraseroGrowisofs stderr: Done with: Version block                           Block(s)    1
BraseroGrowisofs stderr: Writing:   Path table                              Start Block 20
BraseroGrowisofs stderr: Done with: Path table                              Block(s)    4
BraseroGrowisofs stderr: Writing:   Joliet path table                       Start Block 24
BraseroGrowisofs stderr: Done with: Joliet path table                       Block(s)    4
BraseroGrowisofs stderr: Writing:   Directory tree                          Start Block 28
BraseroGrowisofs stderr: Done with: Directory tree                          Block(s)    3
BraseroGrowisofs stderr: Writing:   Joliet directory tree                   Start Block 31
BraseroGrowisofs stderr: Done with: Joliet directory tree                   Block(s)    2
BraseroGrowisofs stderr: Writing:   Directory tree cleanup                  Start Block 33
BraseroGrowisofs stderr: Done with: Directory tree cleanup                  Block(s)    0
BraseroGrowisofs stderr: Writing:   Extension record                        Start Block 33
BraseroGrowisofs stderr: Done with: Extension record                        Block(s)    1
BraseroGrowisofs stderr: Writing:   The File(s)                             Start Block 34
BraseroGrowisofs stderr:   0.25% done, estimate finish Tue Jun 24 09:19:29 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   0.51% done, estimate finish Tue Jun 24 09:19:30 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   0.76% done, estimate finish Tue Jun 24 09:17:18 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 8.2x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=300h failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs stderr: /dev/scd0: flushing cache
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_set_current_action
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2270)

---

### Post by VMC on 2008-06-23
I will point you to a link with almost the exact same message as yours. Maybe it will provide clues for you:
[http://ubuntuforums.org/showthread.php?p=5200205](http://ubuntuforums.org/showthread.php?p=5200205)

Also from Terminal type this:

```
wodim -scanbus
```

It will tell you your DVD ROM drive

---

### Post by Taxman415a on 2008-06-23
The crux of your error looks like this part: 

BraseroGrowisofs stderr: :-[ WRITE@LBA=300h failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
BraseroGrowisofs stderr: write failed: Input/output error

which seems like a hardware error to me on first glance without more information about your drive, the disks you use and what else you've tried. I also don't know what those error codes are, but some googling should be able to tell you. (The failed with part)

So here are the basic steps to try:
1) Try burning at a slower speed
2) Try different, higher quality media

Also you could try choosing file image as your burner for the first step after clicking the burn button in order to create an iso image then try selecting and burning that. It's not likely that's the problem, but at least it would separate the issues. Finally you could try installing another burning application like K3b, but it may require downloading a lot of dependencies if you haven't already installed some KDE stuff. And also there's always the possibility it's the drive. Do you have another one to test with by chance?

---

### Post by muzikoverdose on 2008-06-24
wodim gives me

'MATSHITA' 'DVD-RAM UJ-840S ' '1.00' Removable CD-ROM

i'll try the other options and let you know what it gives me

---

### Post by muzikoverdose on 2008-06-24
I tried making an ISO first and then burning that. i got "Unknown error, check your disc"

its a new Verbatim DVD+R 16x.  this time i was trying to burn 3x, burnproof, increase windows compatibility

---

### Post by Taxman415a on 2008-06-24
> **muzikoverdose said:**
> I tried making an ISO first and then burning that. i got "Unknown error, check your disc"

its a new Verbatim DVD+R 16x.  this time i was trying to burn 3x, burnproof, increase windows compatibility

Yeah makes it sound more like a drive or disc problem then. The detailed output may have been good here too. Changing discs and drives and OSs is the best way to figure out the problem and is about all there is left to test now. If it works in another OS it doesn't mean for sure it's not a hardware problem, as problems can surface in strange ways. Bummer, it sucks when stuff like this doesn't work.

---

### Post by muzikoverdose on 2008-06-25
it seems to be the discs. i tried it with an old CD-RW (yeah, they still exist :) and it burnt an avi file first go.  so, yay for bunk media :) thanks for all the help.

---

### Post by Taxman415a on 2008-06-25
> it seems to be the discs. i tried it with an old CD-RW (yeah, they still exist :) and it burnt an avi file first go.  so, yay for bunk media :) thanks for all the help.

Well, at least it wasn't the drive! Discs are cheaper.

---

### Post by sebutler2 on 2008-07-08
Using a lower burn speed does not resolve this issue.

---

