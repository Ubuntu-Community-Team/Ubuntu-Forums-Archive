---
title: "Brasero Error While Burning (Unhandled error aborting) details inside please help!"
date: 2008-06-17
forum: General Help
---

### Post by Javed_Ahamed on 2008-06-17
Hi guys, ive done some successful burns with brasero with this burner before so im not sure what the problem is now... All my last 4 dvds have gotten this same error message: Unhandeled error aborting (log below) and I dont know what the problem is. Ive tried mixing up the files and dvd brands too.

> Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
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
...list of files to be burned excluded
Padblock                        Start Block 0
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
BraseroGrowisofs stderr: Done with: Directory tree                          Block(s)    62
BraseroGrowisofs stderr: Writing:   Joliet directory tree                   Start Block 90
BraseroGrowisofs stderr: Done with: Joliet directory tree                   Block(s)    50
BraseroGrowisofs stderr: Writing:   Directory tree cleanup                  Start Block 140
BraseroGrowisofs stderr: Done with: Directory tree cleanup                  Block(s)    0
BraseroGrowisofs stderr: Writing:   Extension record                        Start Block 140
BraseroGrowisofs stderr: Done with: Extension record                        Block(s)    1
BraseroGrowisofs stderr: Writing:   The File(s)                             Start Block 141
BraseroGrowisofs stderr:   0.33% done, estimate finish Tue Jun 17 21:05:08 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   0.67% done, estimate finish Tue Jun 17 21:05:07 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   1.00% done, estimate finish Tue Jun 17 21:03:28 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: /dev/scd0: engaging DVD-R DAO upon user request...
BraseroGrowisofs stderr: :-[ PERFORM OPC failed with SK=3h/ASC=11h/ACQ=00h]: Input/output error
BraseroGrowisofs stderr: /dev/scd0: reserving 1501567 blocks
BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 8.2x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2270)


---

### Post by milot on 2008-10-27
Same problem here after my Ubuntu 8.10 upgrade

---

### Post by kurtdriver on 2008-10-28
Did you get an error message? Trying to burn a 3.8 gig iso in brasero produces "insufficient space on media", and even prior to clicking "burn" brasero says Oversized(3.8 gigs in DVD-RAM GH22NP20). But it also reprts that "The medium can be recorded". I am at a loss!

---

### Post by drdread on 2008-10-30
I too had upgraded from gutsy to hardy and found was unable to burn,
much reading in forums etc, decided to install gnomebaker, success! 
so I am guessing that experimentation is the way!
am loving ubuntu! after win xp

---

### Post by gmjs on 2008-10-30
Yes - I've just wasted two CDs in Brasero in Ubuntu 8.10.

---

### Post by JECHO on 2008-11-01
yeah im having pretty much the same problem... i try to burn audio cds and get this message even though its a brand new blank CD-R. 

"Insufficient space on media (0 available for 256289)"


...I've tried 3 or 4 disks and still am getting this message. I've used Brasero while on Hardy without a problem. After doing a clean install of Intrepid now it doesn't work :(

hopefully this bug is fixed soon:confused:

---

### Post by qwerty108109 on 2008-11-11
I am having trouble burning dc+r on ubuntu.  I don't know what the heck it's putting on them, but it's certainly not my ISO image of ubuntu. I hope if this gets enough responses this bug will be fixed. ](*,)

---

### Post by Bobrm2 on 2008-11-16
Having the same problem, in Brasero, I've downloaded and ran GnomeBaker; with the following result.

: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Directories too deep for '.mozilla-thunderbird/profile/ol20wxi8.slt/Mail/mail.alltel.com/Inbox.sbd/Security.sbd/GPG.sbd' (7) max is 6.
gpass

Going back to GnomeBaker to see if I can locate where to set the charset (UTF-8 is the correct setting for my configuration).   I am asked if I wish to "Add" or Not Add" several .sbd.

This may shed a clue to someone more familar with the burning process.

Your help/comments appreciated.

Bob

---

### Post by citizenchris099 on 2008-11-18
running brasero 0.8.2

i started last night burning a dvd iso w/o any problems. 
after that tried burning an audio cd and got the insufficient space error.
then tried burning a data dvd and received the same message. 
installed gnomebaker and ....viola same message. 
dont know what that means but it seems to point to the fact that its not specific to the application.
check out the following links...supposedly a new version of brasero is about to drop.
[http://ftp.gnome.org/pub/GNOME/sources/brasero/0.8/brasero-0.8.3.news](http://ftp.gnome.org/pub/GNOME/sources/brasero/0.8/brasero-0.8.3.news)

[http://bugzilla.gnome.org/show_bug.cgi?id=556449](http://bugzilla.gnome.org/show_bug.cgi?id=556449)

---

### Post by SeaJayEmm on 2008-11-30
For everyone having problems burning DVD's try this. 
Use K3b (sudo apt-get install k3b, if you dont have it already)
Change the write speed (set to Auto by default) to the lowest speed possible
BadaBingBadaBoom it works!

This worked for me, I have Ubuntu 8.10 (Intrepid) installed and couldn't burn a dvd with any program (K3b, Brasero, CD/DVD Creator). After doing the above it has worked everytime no problem. Then find the maximum speed it will burn correctly with and you are good to go. Hope this works for someone else, I searched and searched looking for an answer and couldn't find one, so hopefully this saves someone somewhere some time. Thanks -Justin

---

### Post by nmvictor on 2009-02-07
[FONT="Georgia"]I though this was just about me :obut I now know that its a common problem to almost all ubuntu 8.10 users.however,mine is quit different.This is the session log[/FONT][FONT="Courier New"][HTML]BraseroCdrdao stderr: 66:58:00
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_set_written_track
BraseroCdrdao called brasero_job_start_progress
BraseroCdrdao stderr: 66:59:00
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_set_written_track
BraseroCdrdao called brasero_job_start_progress
BraseroCdrdao stderr: 67:00:00
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_set_written_track
BraseroCdrdao called brasero_job_start_progress
BraseroCdrdao stderr: 67:01:00

BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_set_written_track
BraseroCdrdao called brasero_job_start_progress
BraseroCdrdao stderr: Reading of toc and track data finished successfully.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao stderr: HUP
BraseroCdrdao process finished with status 0
BraseroCdrdao called brasero_job_get_fd_out
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_output_type
BraseroCdrdao called brasero_job_get_image_output
BraseroCdrdao called brasero_job_add_track
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao finished successfully session
BraseroCdrdao stopping
BraseroCdrdao got killed
Checking session consistency (brasero_burn_check_session_consistency burn.c:1843)
Checking session consistency (brasero_burn_check_session_consistency burn.c:1843)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_950XNU.toc toc = /tmp/brasero_tmp_950XNU
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao getting varg
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao got varg:
BraseroCdrdao deactivating
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao stopping
Session error : Insufficient space on media (0 available for 301638) (brasero_burn_record burn.c:2524)[/HTML][/FONT].I just hope that if this is a bug,it gets fixed because I have grown to like brasero and I cant imagine dong without it.

---

### Post by sr4794 on 2009-03-16
I have had the same problem with Brasero and the standard Gnome burning program while trying to burn iso images. I am using 8x DVD+R discs and usually set the buring speed to 'maximum possible'. However unhandled errors pop up left right and centre. 

The solution for me was to choose to burn at the slowest possible speed (2.4x). Its a bummer being so slow but it works. No more error messages!

Hope this helps.

---

### Post by scottkicksbutt on 2009-03-25
I have had success burning ISO images by lowering the burn speed from 8 (max) to 4 running ubuntu 8.10 on a IBM thinkpad t60p using both brasero and from the command line using dvd record.

In brasero, start a new project, choose the iso, and then click properties button to the right of the cd/dvd drive.  Choose the lowest speed listed and burn the project.

I use the following for dvd record but syntax may differ according to your setup.

dvdrecord -v driveropts=burnfree speed=4 dev=/dev/dvd  ~/debian-5.0.iso

---

### Post by johnswb on 2009-12-30
I'm getting the same thing here running Ubuntu 9.10...  I'm only trying to burn and iso image that is less then 700MB.


> BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: F1 00 03 00 01 6A 1C 0A 00 2B 00 00 0C 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x3 Medium Error, deferred error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 92700 (valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 5.116s timeout 40s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:  182 of  552 MB written (fifo 100%) [buf 100%]  12.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: write track data: error after 191098880 bytes
BraseroWodim stdout: Writing  time:  128.763s
BraseroWodim stdout: Average write speed  30.1x.
BraseroWodim stdout: Min drive buffer fill was 98%
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Fixating time:   31.291s
BraseroWodim stderr: wodim: fifo had 3265 puts and 3011 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo was 0 times empty and 2997 times full, min fill was 97%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: BURN-Free was never needed.
BraseroWodim stderr: HUP
BraseroWodim stdout: HUP
BraseroWodim process finished with status 254
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2811)

---

