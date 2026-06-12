---
title: "k3b burning failed- cdrecord has no permission to open the device"
date: 2007-12-15
forum: General Help
---

### Post by hrabeX on 2007-12-15
I've tried to burn an audio cd, after reaching cca 9 % (finishing 1st track) k3b stops burning and give me this message:
"cdrecord has no permission to open the device"
and log:
System
```
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
MATSHITA UJ-840D 1.00 (/dev/hdd, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, Restricted Overwrite]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identification : 'UJ-840D         '
Revision       : '1.00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO
Drive buf size : 1310720 = 1280 KB
FIFO size      : 12582912 = 12288 KB
pregap1: -1
Track 01: audio   41 MB (04:06.78) no preemp swab copy
Track 02: audio   36 MB (03:36.09) no preemp swab copy
Track 03: audio   40 MB (04:03.62) no preemp swab copy
Track 04: audio   37 MB (03:42.72) no preemp swab copy
Track 05: audio   41 MB (04:05.21) no preemp swab copy
Track 06: audio   46 MB (04:38.40) no preemp swab copy
Track 07: audio   41 MB (04:06.00) no preemp swab copy
Track 08: audio   36 MB (03:38.25) no preemp swab copy
Track 09: audio   47 MB (04:44.72) no preemp swab copy
Track 10: audio   36 MB (03:34.24) no preemp swab copy
Track 11: audio   39 MB (03:51.86) no preemp swab copy
Total size:      445 MB (44:07.92) = 198594 sectors
Lout start:      445 MB (44:09/69) = 198594 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11077 (97:34/23)
  ATIP start of lead out: 359848 (79:59/73)
Speed set to 4234 KB/s
Disk type:    Long strategy type (Cyanine, AZO or similar)
Manuf. index: 11
Manufacturer: Mitsubishi Chemical Corporation
Blocks total: 359848 Blocks current: 359848 Blocks remaining: 161254
Starting to write CD/DVD at speed  24.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of   41 MB written.
Track 01:    1 of   41 MB written (fifo 100%) [buf  99%]   7.9x.
Track 01:    2 of   41 MB written (fifo 100%) [buf  98%]   8.1x.
Track 01:    3 of   41 MB written (fifo 100%) [buf  98%]   8.5x.
Track 01:    4 of   41 MB written (fifo 100%) [buf 100%]   8.4x.
Track 01:    5 of   41 MB written (fifo 100%) [buf 100%]   8.5x.
Track 01:    6 of   41 MB written (fifo 100%) [buf  99%]   8.1x.
Track 01:    7 of   41 MB written (fifo 100%) [buf  99%]   8.5x.
Track 01:    8 of   41 MB written (fifo 100%) [buf  98%]   8.1x.
Track 01:    9 of   41 MB written (fifo 100%) [buf  98%]   8.4x.
Track 01:   10 of   41 MB written (fifo 100%) [buf  97%]   8.1x.
Track 01:   11 of   41 MB written (fifo 100%) [buf  97%]   8.4x.
Track 01:   12 of   41 MB written (fifo 100%) [buf  99%]   8.3x.
Track 01:   13 of   41 MB written (fifo 100%) [buf  99%]   8.4x.
Track 01:   14 of   41 MB written (fifo 100%) [buf  98%]   8.1x.
Track 01:   15 of   41 MB written (fifo 100%) [buf  98%]   8.4x.
Track 01:   16 of   41 MB written (fifo 100%) [buf  97%]   8.0x.
Track 01:   17 of   41 MB written (fifo 100%) [buf  97%]   8.4x.
Track 01:   18 of   41 MB written (fifo 100%) [buf  99%]   8.3x.
Track 01:   19 of   41 MB written (fifo 100%) [buf  99%]   8.4x.
Track 01:   20 of   41 MB written (fifo 100%) [buf  98%]   8.0x.
Track 01:   21 of   41 MB written (fifo 100%) [buf  98%]   8.4x.
Track 01:   22 of   41 MB written (fifo 100%) [buf  97%]   8.0x.
Track 01:   23 of   41 MB written (fifo 100%) [buf  97%]   8.4x.
Track 01:   24 of   41 MB written (fifo 100%) [buf  99%]   8.3x.
Track 01:   25 of   41 MB written (fifo 100%) [buf  99%]   8.3x.
Track 01:   26 of   41 MB written (fifo 100%) [buf  98%]   8.0x.
Track 01:   27 of   41 MB written (fifo 100%) [buf  98%]   8.3x.
Track 01:   28 of   41 MB written (fifo 100%) [buf  98%]   8.0x.
Track 01:   29 of   41 MB written (fifo 100%) [buf  98%]   8.3x.
Track 01:   30 of   41 MB written (fifo 100%) [buf  99%]   8.3x.
Track 01:   31 of   41 MB written (fifo 100%) [buf  99%]   8.3x.
Track 01:   32 of   41 MB written (fifo 100%) [buf  99%]   8.0x.
Track 01:   33 of   41 MB written (fifo 100%) [buf  99%]   8.3x.
Track 01:   34 of   41 MB written (fifo 100%) [buf  98%]   8.0x.
Track 01:   35 of   41 MB written (fifo 100%) [buf  98%]   8.3x.
Track 01:   36 of   41 MB written (fifo 100%) [buf 100%]   8.2x.
Track 01:   37 of   41 MB written (fifo 100%) [buf 100%]   8.3x.
Track 01:   38 of   41 MB written (fifo 100%) [buf  99%]   7.9x.
Track 01:   39 of   41 MB written (fifo 100%) [buf  99%]   8.2x.
Track 01:   40 of   41 MB written (fifo 100%) [buf  98%]   7.9x.
Errno: 0 (Success), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 47 4C 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F1 00 03 00 00 44 D9 0A 00 2B 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 17625 (valid) 
resid: 63504
cmd finished after 5.117s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 42928704 bytes
Writing  time:   61.990s
Average write speed  45.3x.
Min drive buffer fill was 97%
Fixating...
Fixating time:    0.005s
/usr/bin/wodim: fifo had 868 puts and 677 gets.
/usr/bin/wodim: fifo was 0 times empty and 676 times full, min fill was 99%.
BURN-Free was never needed.


```

please help.

---

### Post by snowbum45 on 2007-12-19
Go to kcontrol > administrtation > disk and filesystems 
find the /dev/xxxx for your cd writer drive
then open up a command prompt like konsole and type

sudo chmod 777 /dev/xxxx

that changes the permissions for the device and should let you do it

---

### Post by maestrobwh1 on 2007-12-19
This just sort of crops up from time to time.  Why is this?

---

### Post by styrofoam cup on 2007-12-22
I got the same problem after my latest upgrade (included kernel update) Was working fine before that.
I followed the instructions above for the chmod, but the device listed (by following the instructions) was the wrong one. I found the right device by looking at the log 'show debugging output' log created by kb3. 
seems to be working fone now. 

Thanks to everyone.

---

### Post by mangaman on 2007-12-23
I get the same problem, "Cannot raise RLIMIT_MEMLOCK limits.". 
I have tried

sudo chmod 777 /dev/scd0 

scd0 happens to be my dvd burner, and I still get the same problem. i have also tried to run k3b as root (sudo k3b)
Anymore suggestions?
Thanks

---

### Post by Motorhead Kaze on 2008-01-23
I have this problem too!  Where is this "Kcontrol/admin" you speak of?  I'm in Gutsy, is that only for Kubuntu people?

Also, if I need to do something with the log, where do I find that?  I have been having a really tweeked time with my DVD/Cd player this week, and K3b is saying all sorts of things like "Can't copy encrypted disc" and "Cd record has no permission to open device."

I would really appreciate it if you'd tell me where to find this menu.

Thanks in advance!
Carl

---

### Post by crafter on 2008-01-26
Look here: [https://answers.launchpad.net/ubuntu/+source/k3b/+question/21117]("https://answers.launchpad.net/ubuntu/+source/k3b/+question/21117")

---

### Post by Motorhead Kaze on 2008-01-26
Hello.

I have just grabbed Kcontrol, and am trying to follow the above instructions
Go to kcontrol > administrtation > disk and filesystems
find the /dev/xxxx for your cd writer drive
then open up a command prompt like konsole and type

sudo chmod 777 /dev/xxxx

kcontrol/system administration/ there is no disk and file systems option.  There ARE:
Date and time, font installer, login manager and paths

In Paths, there is desktop, autostart and documents.  Am I missing something?

Thanks I looked here: [https://answers.launchpad.net/ubuntu...question/21117](https://answers.launchpad.net/ubuntu...question/21117) followed all that.  Everything seems to be fine according to that post.

---

### Post by lucas42 on 2008-02-21
Hi,
    I'm getting the same error despite my permissions being fine.  If i check `ls -l /dev/cd*` it returns:
```

lrwxrwxrwx 1 root root 3 2008-02-21 23:08 /dev/cdrom -> hdd
lrwxrwxrwx 1 root root 3 2008-02-21 23:08 /dev/cdrw -> hdd

```
I'm not sure if those symlinks should be there.
The only real difference I spotted between my debugging ouput and the one above is
Sense Key: 0x4 Hardware Error, Segment 0
and
Sense flags: Blk 0 (not valid) 

Perhaps this is something completely unconnected then, I'm not sure

Thanks.

---

### Post by river2884 on 2008-02-21
K3b is a piece of ****.

---

### Post by lucas42 on 2008-02-21
Any suggestions for something that'll let me burn .iso images quickly without too much to setup?  I only tried K3b because it was already on kUbuntu.

---

### Post by bruceleo on 2008-03-11
I tried all of these things and nothing worked. I finally figured out that the .cue file I was trying to burn had the bin file name in caps. Open the .cue file in text editor and check that the .bin file name is correct (cap dependent).

---

### Post by Stu284 on 2008-03-30
i am having the same problem trying to burn a divx file to a cd with k3b,  the annoying thing is it works fine in simulate!! i have changed the program user perimiters in k3b and this just gave me the error sooner and wasted another cd  :(

just seems strange it works fine in simulate and it does not give the error until it has burned about a 1/3 of the cd?

---

### Post by skullmunky on 2008-05-27
I'm having this same problem trying to do an audio CD disc copy, right at the beginning of the burn process.  It doesn't happen all the time - often I can burn 20, 30 discs, then suddenly this error appears and I can't burn anymore.  Device permissions are fine (I'm in the cdrom group, and I also chmod'd the device just to make sure

```

lrwxrwxrwx 1 root root 4 2008-05-26 12:45 cdrom -> scd0
brwxrwxrwx+ 1 root cdrom 11, 0 2008-05-26 12:45 scd0

```

I then tried burning using Brasero, similar error.

K3B output is below.  Do you think one of these might be relevant?

```

/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.

/usr/bin/wodim: WARNING: Drive returns wrong startsec (-150) using -11634 from ATIP
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error


```

```

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-16-generic
Devices
-----------------------
PIONEER DVD-RW  DVR-109 1.17 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-109 '
Revision       : '1.17'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 12582912 = 12288 KB
Encoding speed : 271x (20312 sectors/s) for libedc from Heiko Eißfeldt
pregap1: -1
Track 01: audio  100 MB (09:57.36) no preemp copy
Track 02: audio   79 MB (07:54.84) no preemp copy pregapsize:   0
Track 03: audio   83 MB (08:13.68) no preemp copy pregapsize:   0
Track 04: audio   75 MB (07:27.73) no preemp copy pregapsize:   0
Track 05: audio   56 MB (05:38.44) no preemp copy pregapsize:   0
Track 06: audio   66 MB (06:33.02) no preemp copy pregapsize:   0
Track 07: audio  112 MB (11:09.85) no preemp copy pregapsize:   0
Track 08: audio   67 MB (06:43.61) no preemp copy pregapsize:   0
Track 09: audio   90 MB (08:56.20) no preemp copy pregapsize:   0
Total size:      732 MB (72:34.74) = 326606 sectors
Lout start:      732 MB (72:36/56) = 326606 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Speed set to 5644 KB/s
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 33240
Starting to write CD/DVD at speed  32.0 in real RAW/RAW96R mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
/usr/bin/wodim: WARNING: Drive returns wrong startsec (-150) using -11634 from ATIP
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 FF FF E6 5C 00 00 1A 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 71 00 03 00 98 32 21 0E 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 9974305 (not valid) 
cmd finished after 0.001s timeout 40s
/usr/bin/wodim: Could not write Lead-in.
Writing lead-in at sector -11634
write leadin data: error after 12411360 bytes
Writing  time:   33.249s
/usr/bin/wodim: fifo had 192 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=32 -raw96r driveropts=burnfree -eject -overburn -text -useinfo -audio -shorttrack /tmp/k3bCdCopy0/Track01.wav /tmp/k3bCdCopy0/Track02.wav /tmp/k3bCdCopy0/Track03.wav /tmp/k3bCdCopy0/Track04.wav /tmp/k3bCdCopy0/Track05.wav /tmp/k3bCdCopy0/Track06.wav /tmp/k3bCdCopy0/Track07.wav /tmp/k3bCdCopy0/Track08.wav /tmp/k3bCdCopy0/Track09.wav 


```

---

