---
title: "Feisty k3b burns empy disks, no errors"
date: 2007-04-27
forum: General Help
---

### Post by midden on 2007-04-27
Hi all,

I recently upgraded from my Lenovo T60 from Edgy to Feisty. Although I had never tried the cd/dvd burner while running Edgy, after the upgrade I successfully burned a data DVD and a CD from ISO using K3B (I had to use cdrskin and set the cdrecord parameters to, "-v dev_translation=+/dev/scd0+/dev/sg0"). However, I tried to burn another disk today (the Feisty ISO in fact, and yes the Md5Sums check out), and despite K3B declaring success, the disk was only partially burned (i.e., ~ 3 mm of tracks visible on the burned surface rendering the disk useless). I tried to burn a data CD and had the same result--- the drive spins throughout the whole process, but the drive light is only on for a few seconds of the burn. The other weird things are that the average speed is > 140x and during the burn, the device buffer never goes above 50%. I get the same results in real and simulate modes using 4x, 10x, and 24x burn speeds (I am accumulating quite a large pile of coasters made of the same media I used for my previous, successful burns). Does anybody have suggestions on how to fix this? I could never get Gnomebaker or XCDroast to work on Feisty, so I am mostly interested in getting K3B back online. I have attached the log file in case it will help diagnose the problem. Thanks for your help.

Cheers,

midden

```
System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-15-generic
Devices
-----------------------
HL-DT-ST DVDRAM GSA-4083N 1.08 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Used versions
-----------------------
cdrecord: 2.1-Emulation

cdrecord
-----------------------
cdrskin 0.2.2 : limited cdrecord compatibility wrapper for libburn
cdrskin: initializing libburn ... ok
cdrskin: NOTE : greying out all drives besides given dev='/dev/sg0'
cdrskin: scanning for devices ...
 done
cdrskin: verbosity level : 1
cdrskin: verbosity level : 2
cdrskin: fixed track size : 731797504
cdrskin: track 1 data source : '-'  (i.e. standard input)
cdrskin: installed hard abort handler.
cdrskin: dev_translation=... :  dev='/dev/scd0' to dev='/dev/sg0'
cdrskin: active drive number : 0  '/dev/sg0'
cdrskin: establishing fifo of 4194304 bytes
cdrskin: called as :  /usr/bin/cdrskin
cdrskin: beginning to burn disk
cdrskin: status 1 burn_disc_blank "The drive holds a blank disc"
Track 01: data   697 MB        
Total size:      697 MB (79:26.30) = 357323 sectors
Lout start:      697 MB (79:28/30) = 357323 sectors
Starting to write CD/DVD at speed 10 in real SAO mode for single session.
Last chance to quit, starting real write in   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
cdrskin: thank you for being patient since 0 seconds                   
cdrskin: thank you for being patient since 1 seconds                   
cdrskin: thank you for being patient since 2 seconds                   

 <snip>

cdrskin: thank you for being patient since 35 seconds                   
cdrskin: thank you for being patient since 36 seconds                   
cdrskin: thank you for being patient since 37 seconds                   
cdrskin: thank you for being patient since 39 seconds                   
Starting new track at sector: 0
                                                                              
Track 01:    1 of  697 MB written (fifo 100%) [buf  50%]  19.4x.
Track 01:    2 of  697 MB written (fifo 100%) [buf  50%]  131.4x.
Track 01:    3 of  697 MB written (fifo 100%) [buf  50%]  152.9x.
Track 01:    4 of  697 MB written (fifo 100%) [buf  50%]  153.6x.

.<snip>

Track 01:  695 of  697 MB written (fifo 100%) [buf  50%]  157.9x.
Track 01:  696 of  697 MB written (fifo 100%) [buf  50%]  151.3x.
Track 01:  697 of  697 MB written (fifo 100%) [buf  50%]  152.8x.
cdrskin: thank you for being patient since 40 seconds                   
cdrskin: thank you for being patient since 72 seconds                   Cdrskin: fifo had 359745 puts and 357323 gets.
Cdrskin: fifo was 0 times empty and 15635 times full, min fill was 96%.
Track 01: Total bytes read/written: 731136000/731136000 (357000 sectors).
Writing  time:  73.326s
Min drive buffer fill was 50%
cdrskin: burning done

cdrecord command:
-----------------------
/usr/bin/cdrskin -v gracetime=2 dev=/dev/scd0 speed=10 driveropts=burnfree -v dev_translation=+/dev/scd0+/dev/sg0 -data -tsize=357323s - 

```

---

### Post by midden on 2007-05-01
Still no ideas? At this point I am pretty open to suggestions.

Cheers.

midden

---

### Post by Pygi on 2007-05-05
Hi midden,

so let's play :) At this point libburn/cdrskin in repositories of feisty are seriously outdated (2.2 vs. newest 0.3.6), but I'm after it for Gutsy. Would you mind manually installing from source?

Grab the tarball: [http://libburnia-download.pykix.org/releases/libburn-0.3.6.tar.gz](http://libburnia-download.pykix.org/releases/libburn-0.3.6.tar.gz)

For some general idea on how to configure k3b to use cdrskin, please refer to:
[http://scdbackup.sourceforge.net/k3b_on_cdrskin.html](http://scdbackup.sourceforge.net/k3b_on_cdrskin.html)

Regarding the device buffer in 0.2.2 I believe in that version the proper buffer support
didn't existed. We declared just enough of buffer to continue sending the data to drive.

Regarding the speeds shown to you, that is a HAL problem and I believe is
connected to K3b here since cdrskin/libburn don't even touch HAL.

If you've got any questions, please don't hesitate to ask.

KR,
M.

---

### Post by midden on 2007-05-11
Thanks for your suggestion Pygi. I removed the old version of cdrskin and then installed the version you suggested from source. After I added /usr/local/bin/cdrskin to the search path of Kb3, I tried to simulate a burn. This failed, but I tried a real disk just in case. The error log is below. Do you have any suggestions?

Cheers,

midden


```
System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-15-generic
Devices
-----------------------
HL-DT-ST DVDRAM GSA-4083N 1.08 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Used versions
-----------------------
cdrecord: 2.1-Emulation

cdrecord
-----------------------
cdrskin 0.3.6 : limited cdrecord compatibility wrapper for libburn
cdrskin: verbosity level : 1
cdrskin: NOTE : greying out all drives besides given dev='/dev/sr0'
cdrskin: scanning for devices ...
cdrskin: ... scanning for devices done
cdrskin: beginning to burn disc
cdrskin: status 1 burn_disc_blank "The drive holds a blank disc"
Track 01: data   697 MB        
Total size:      697 MB (79:26.30) = 357323 sectors
Lout start:      697 MB (79:28/30) = 357323 sectors
Starting to write CD/DVD at speed 10 in real SAO mode for single session.
Last chance to quit, starting real write in   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
cdrskin: working pre-track (burning since 1 seconds)         
cdrskin: working pre-track (burning since 2 seconds)         
cdrskin: working pre-track (burning since 3 seconds)         
cdrskin: working pre-track (burning since 4 seconds)         
cdrskin: working pre-track (burning since 5 seconds)         
cdrskin: working pre-track (burning since 6 seconds)         
cdrskin: working pre-track (burning since 7 seconds)         
cdrskin: working pre-track (burning since 8 seconds)         
cdrskin: working pre-track (burning since 9 seconds)         
cdrskin: working pre-track (burning since 10 seconds)         
cdrskin: working pre-track (burning since 11 seconds)         
cdrskin: working pre-track (burning since 12 seconds)         
cdrskin: working pre-track (burning since 13 seconds)         
cdrskin: working pre-track (burning since 14 seconds)         
cdrskin: working pre-track (burning since 15 seconds)         
cdrskin: working pre-track (burning since 16 seconds)         
cdrskin: working pre-track (burning since 17 seconds)         
cdrskin: working pre-track (burning since 18 seconds)         
cdrskin: working pre-track (burning since 19 seconds)         
cdrskin: working pre-track (burning since 20 seconds)         
cdrskin: working pre-track (burning since 21 seconds)         
cdrskin: working pre-track (burning since 22 seconds)         
cdrskin: working pre-track (burning since 23 seconds)         
cdrskin: working pre-track (burning since 24 seconds)         
cdrskin: working pre-track (burning since 25 seconds)         
cdrskin: working pre-track (burning since 26 seconds)         
cdrskin: working pre-track (burning since 27 seconds)         
cdrskin: working pre-track (burning since 28 seconds)         
cdrskin: working pre-track (burning since 29 seconds)         
cdrskin: working pre-track (burning since 30 seconds)         
cdrskin: working pre-track (burning since 31 seconds)         
cdrskin: working pre-track (burning since 32 seconds)         
cdrskin: working pre-track (burning since 33 seconds)         
cdrskin: working pre-track (burning since 34 seconds)         
cdrskin: working pre-track (burning since 35 seconds)         
cdrskin: working pre-track (burning since 36 seconds)         
cdrskin: working pre-track (burning since 37 seconds)         
cdrskin: working pre-track (burning since 38 seconds)         cdrskin: FATAL : SCSI error on write(-150,32): key=5 asc=30h ascq=05h
cdrskin: working pre-track (burning since 39 seconds)         cdrskin: FATAL : Burn run failed
Starting new track at sector: 0
Track 01: Total bytes read/written: 0/0 (0 sectors).
Writing  time:  39.787s
Cdrskin: fifo had 2079 puts and 31 gets.
Cdrskin: fifo was 0 times empty and 0 times full, min fill was 100%.
cdrskin: FATAL : burning failed.
Min drive buffer fill was 50%
cdrskin: burning failed

cdrecord command:
-----------------------
/usr/local/bin/cdrskin -v gracetime=2 dev=/dev/scd0 speed=10 -dao driveropts=burnfree -data -tsize=357323s - 


```

---

### Post by Pygi on 2007-05-11
Hi midden,

would you mind manually burning iso with cdrskin from command line?
Let's see if that will work.

KR,
M.

---

### Post by midden on 2007-05-11
Hi Pygi,
Thanks for getting back with me so fast. I tried the command line and only produced another coaster; however, this is the first time I have tried burning this way, so maybe my command was not quite right.

Cheers,

midden


```
$ sudo cdrskin -v dev=/dev/sr0 speed=12 fs=8m -sao -eject padsize=300k ubuntu-7.04-desktop-i386.iso 
cdrskin 0.3.6 : limited cdrecord compatibility wrapper for libburn
cdrskin: verbosity level : 1
cdrskin: NOTE : greying out all drives besides given dev='/dev/sr0'
cdrskin: scanning for devices ...
cdrskin: ... scanning for devices done
cdrskin: beginning to burn disc
cdrskin: status 1 burn_disc_blank "The drive holds a blank disc"
Track 01: data   697 MB         padsize:  300 KB
Total size:      698 MB (79:28.30) = 357473 sectors
Lout start:      698 MB (79:30/30) = 357473 sectors
Starting to write CD/DVD at speed 12 in real SAO mode for single session.
Last chance to quit, starting real write in   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Starting new track at sector: 0
cdrskin: working pre-track (burning since 39 seconds)         cdrskin: FATAL : SCSI error on write(-150,32): key=5 asc=30h ascq=05h
cdrskin: FATAL : Burn run failed

Track 01: Total bytes read/written: 0/0 (0 sectors).
Writing  time:  40.039s
Cdrskin: fifo had 4127 puts and 31 gets.
Cdrskin: fifo was 0 times empty and 0 times full, min fill was 100%.
Min drive buffer fill was 50%
cdrskin: burning failed
cdrskin: FATAL : burning failed.

```

---

### Post by Pygi on 2007-05-11
Hi,

Sorry for not really looking at your debug outputs before.

```
cdrskin: working pre-track (burning since 39 seconds)         cdrskin: FATAL : SCSI error on write(-150,32): key=5 asc=30h ascq=05h
```

According to MMC5, this would mean that the format is incompatible.

5 30 05 CANNOT WRITE MEDIUM  INCOMPATIBLE FORMAT

KR,
M.

---

### Post by midden on 2007-05-11
Okay, but as I said in my original post, I have burned onto this media before. One day I can burn, the next day I can't. That indicates to me that something got out of whack during a dist-upgrade. I just don't know what to look for to diagnose the problem.

midden.

---

### Post by midden on 2007-05-16
Hi all,

Let me reiterate that the media I am using are Verbatim CD-Rs that I have burned to without problem before. So I doubt that the media are actually "incompatible". Can anyone suggest what might have broken my ability to burn?

Cheers,

midden

---

### Post by Pygi on 2007-06-08
Hello,

sorry for taking so long to get to you. 
Would you be so kind to provide me the output of:

   test/telltoc --drive /dev/sr0
   cdrskin -vvv -atip dev=/dev/sr0
and (from package dvd+rw-tools):
   dvd+rw-mediainfo /dev/sr0

Thank you.

KR,
M.

---

### Post by longlegs on 2007-06-08
Hi ,
I don't like making coasters so I use cd-RW disks which can be treated just like cd-r's but can be erased after a faulty burn and re-used. When I get things right, THEN i may burn a cd-r if I intend to keep it. 
( have you thought that it might be a SCSI driver problem?)

Good luck with your problem.
longlegs

---

### Post by kelvin spratt on 2007-06-08
you might have a SCSI driver problem? as i use Nero and it does a drive check on start up and says it can't find any SCSI drivers but I Don't need SCSI for my writer, so its not an issue for me in Nero help it says after a certain kernel Linux does not support SCSI by default or words to that effect.

---

### Post by midden on 2007-07-05
Hello,

Somehow, as if by magic, K3B burns for me now (but only under sudo). This is a fairly unsatisfying solution because I don't know what went wrong to begin with, nor how it was fixed. Buried in a dist-upgrade, perhaps? Anyhow, I have included the output of the latter two commands in case you see something that is useful (I am not familiar with the first command "test" does not accept --device and telltoc is not a command on my system). Thanks for your help.

midden


```

$ cdrskin -vvv -atip dev=/dev/sr0
cdrskin 0.3.6 : limited cdrecord compatibility wrapper for libburn
cdrskin: DEBUG : burn_drive_convert_fs_adr( /dev/sr0 )
cdrskin: DEBUG : burn_drive_is_enumerable_adr( /dev/sr0 ) is true
cdrskin: NOTE : greying out all drives besides given dev='/dev/sr0'
cdrskin: scanning for devices ...
cdrskin: ... scanning for devices done
cdrskin: will put out some -atip style lines
cdrskin: installed hard abort handler.
cdrskin: active drive number : 0  '/dev/sr0'
cdrskin: called as :  cdrskin
cdrskin: pseudo-atip on drive 0
cdrskin: status 1 burn_disc_blank "The drive holds a blank disc"
scsidev: '4,0,0'
Device type    : Removable CD-ROM
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GSA-4083N'
Revision       : '1.08'
Driver flags   : BURNFREE
cdrskin_debug: block_types: tao=3F0F  sao=4000  raw=3F0F
Supported modes: TAO SAO RAW/RAW96R
cdrskin: burn_drive_get_write_speed = 4234  (24.0x)
Current: CD-R
ATIP info from disk:
  Is not erasable
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
  1T speed low:  10 1T speed high: 24

```



```

$ dvd+rw-mediainfo /dev/sr0

DiskInfo:
Mediatype:       CD-R
Current Profile: CD-R
Disk state:      empty
Empty:           1
Rewritable:      0
Appendable:      0
Sessions:        0
Tracks:          0
Layers:          1
Capacity:        79:57:71 (LBA 359846) (736964608 Bytes)
Remaining size:  79:57:71 (LBA 359846) (736964608 Bytes)
Used Size:       00:00:00 (LBA 0) (0 Bytes)
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via 2A: 3
(K3bDevice::Device) /dev/scd0 : 4234 KB/s
(K3bDevice::Device) /dev/scd0 : 2823 KB/s
(K3bDevice::Device) /dev/scd0 : 1764 KB/s
adding udi   /org/freedesktop/Hal/devices/volume_empty_cd_r
MediaManager::slotMediumAdded: scd0


```:popcorn:

---

### Post by Pygi on 2007-07-15
"telltoc" binary is located in test/ directory of libburn tarball once you run "make" :)
Thanks for the reply.

---

