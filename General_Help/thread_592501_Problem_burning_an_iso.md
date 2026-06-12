---
title: "Problem burning an iso"
date: 2007-10-26
forum: General Help
---

### Post by TeeAhr1 on 2007-10-26
It's the weirdest thing.  I have no problem burning CDs on this machine, but I've tried three times to burn the xubuntu 7.10 iso, and it's errored out every time.  The file is good, I even re-downloaded it last night just to make sure.  Here's my output:

```
System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
TSSTcorp CDW/DVD SH-M522C TS05 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identification : 'CDW/DVD SH-M522C'
Revision       : 'TS05'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x0009 (CD-R)
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Profile: 0x0010 (DVD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1278464 = 1248 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 8467 KB/s
Track 01: data   566 MB        
Total size:      650 MB (64:26.46) = 289985 sectors
Lout start:      650 MB (64:28/35) = 289985 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359848 (79:59/73)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359848 Blocks current: 359848 Blocks remaining: 69863
Starting to write CD/DVD at speed  48.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  566 MB written.
Track 01:    1 of  566 MB written (fifo  94%) [buf  97%]   0.8x.
Track 01:    2 of  566 MB written (fifo  93%) [buf 100%]  22.1x.
Track 01:    3 of  566 MB written (fifo  93%) [buf 100%]  22.9x.
Track 01:    4 of  566 MB written (fifo  89%) [buf  95%]  22.2x.
Track 01:    5 of  566 MB written (fifo  83%) [buf  97%]  23.0x.
Track 01:    6 of  566 MB written (fifo  78%) [buf 100%]  22.3x.
Track 01:    7 of  566 MB written (fifo  90%) [buf  95%]  23.1x.
Track 01:    8 of  566 MB written (fifo  98%) [buf  99%]  22.5x.
Track 01:    9 of  566 MB written (fifo  99%) [buf 100%]  23.2x.
Track 01:   10 of  566 MB written (fifo 100%) [buf 100%]  22.6x.
Track 01:   11 of  566 MB written (fifo  99%) [buf  94%]  23.3x.
Track 01:   12 of  566 MB written (fifo 100%) [buf  97%]  22.7x.
Track 01:   13 of  566 MB written (fifo 100%) [buf 100%]  23.5x.
Track 01:   14 of  566 MB written (fifo 100%) [buf  99%]  22.8x.
Track 01:   15 of  566 MB written (fifo 100%) [buf 100%]  23.6x.
Track 01:   16 of  566 MB written (fifo 100%) [buf 100%]  22.9x.
Track 01:   17 of  566 MB written (fifo  98%) [buf  96%]  23.7x.
Track 01:   18 of  566 MB written (fifo 100%) [buf 100%]  23.0x.
Track 01:   19 of  566 MB written (fifo 100%) [buf  99%]  23.8x.
Track 01:   20 of  566 MB written (fifo 100%) [buf  99%]  23.2x.
Track 01:   21 of  566 MB written (fifo  99%) [buf 100%]  24.0x.
Track 01:   22 of  566 MB written (fifo 100%) [buf  98%]  23.1x.
Track 01:   23 of  566 MB written (fifo 100%) [buf  96%]  24.2x.
Track 01:   24 of  566 MB written (fifo 100%) [buf 100%]  23.4x.
Track 01:   25 of  566 MB written (fifo 100%) [buf  96%]  24.2x.
Track 01:   26 of  566 MB written (fifo 100%) [buf 100%]  23.5x.
Track 01:   27 of  566 MB written (fifo 100%) [buf  99%]  24.3x.
Track 01:   28 of  566 MB written (fifo 100%) [buf 100%]  23.6x.
Track 01:   29 of  566 MB written (fifo 100%) [buf  96%]  24.3x.
Track 01:   30 of  566 MB written (fifo  98%) [buf  98%]  23.6x.
Track 01:   31 of  566 MB written (fifo 100%) [buf  99%]  24.4x.
Track 01:   32 of  566 MB written (fifo  99%) [buf  97%]  23.7x.
Track 01:   33 of  566 MB written (fifo  99%) [buf 100%]  24.5x.
Track 01:   34 of  566 MB written (fifo 100%) [buf  99%]  25.3x.
Track 01:   35 of  566 MB written (fifo 100%) [buf 100%]  24.5x.
Track 01:   36 of  566 MB written (fifo  98%) [buf  99%]  25.4x.
Track 01:   37 of  566 MB written (fifo  99%) [buf  96%]  24.6x.
Track 01:   38 of  566 MB written (fifo 100%) [buf  99%]  25.4x.
Track 01:   39 of  566 MB written (fifo 100%) [buf 100%]  24.7x.
Track 01:   40 of  566 MB written (fifo 100%) [buf 100%]  25.5x.
Track 01:   41 of  566 MB written (fifo 100%) [buf 100%]  24.8x.
Track 01:   42 of  566 MB written (fifo 100%) [buf  95%]  25.6x.
Track 01:   43 of  566 MB written (fifo 100%) [buf 100%]  24.8x.
Track 01:   44 of  566 MB written (fifo  99%) [buf  99%]  25.7x.
Track 01:   45 of  566 MB written (fifo 100%) [buf 100%]  24.9x.
Track 01:   46 of  566 MB written (fifo  99%) [buf  98%]  25.7x.
Track 01:   47 of  566 MB written (fifo  99%) [buf  94%]  25.0x.
Track 01:   48 of  566 MB written (fifo  98%) [buf 100%]  25.8x.
Track 01:   49 of  566 MB written (fifo 100%) [buf  96%]  25.1x.
Track 01:   50 of  566 MB written (fifo 100%) [buf 100%]  25.9x.
Track 01:   51 of  566 MB written (fifo 100%) [buf 100%]  25.2x.
Track 01:   52 of  566 MB written (fifo 100%) [buf  99%]  25.9x.
Track 01:   53 of  566 MB written (fifo  99%) [buf 100%]  25.3x.
Track 01:   54 of  566 MB written (fifo  97%) [buf 100%]  26.0x.
Track 01:   55 of  566 MB written (fifo  98%) [buf  94%]  25.3x.
Track 01:   56 of  566 MB written (fifo  99%) [buf 100%]  26.1x.
Track 01:   57 of  566 MB written (fifo 100%) [buf  98%]  25.4x.
Track 01:   58 of  566 MB written (fifo 100%) [buf  99%]  26.2x.
Track 01:   59 of  566 MB written (fifo 100%) [buf 100%]  25.4x.
Track 01:   60 of  566 MB written (fifo  99%) [buf 100%]  26.3x.
Track 01:   61 of  566 MB written (fifo 100%) [buf 100%]  25.5x.
Track 01:   62 of  566 MB written (fifo 100%) [buf  99%]  26.3x.
Track 01:   63 of  566 MB written (fifo 100%) [buf  99%]  25.6x.
Track 01:   64 of  566 MB written (fifo 100%) [buf  95%]  26.0x.
Track 01:   65 of  566 MB written (fifo  99%) [buf  98%]  27.6x.
Track 01:   66 of  566 MB written (fifo 100%) [buf  99%]  26.4x.
Track 01:   67 of  566 MB written (fifo 100%) [buf  94%]  27.2x.
Track 01:   68 of  566 MB written (fifo 100%) [buf  97%]  26.6x.
Track 01:   69 of  566 MB written (fifo 100%) [buf 100%]  27.4x.
Track 01:   70 of  566 MB written (fifo 100%) [buf  97%]  26.5x.
Track 01:   71 of  566 MB written (fifo  98%) [buf  93%]  27.3x.
Track 01:   72 of  566 MB written (fifo 100%) [buf  99%]  26.8x.
Track 01:   73 of  566 MB written (fifo 100%) [buf 100%]  27.5x.
Track 01:   74 of  566 MB written (fifo 100%) [buf  99%]  26.7x.
Track 01:   75 of  566 MB written (fifo 100%) [buf  99%]  27.6x.
Track 01:   76 of  566 MB written (fifo 100%) [buf  99%]  26.7x.
Track 01:   77 of  566 MB written (fifo 100%) [buf  99%]  27.6x.
Track 01:   78 of  566 MB written (fifo 100%) [buf 100%]  26.8x.
Track 01:   79 of  566 MB written (fifo  99%) [buf  99%]  27.7x.
Track 01:   80 of  566 MB written (fifo  99%) [buf  99%]  26.9x.
Track 01:   81 of  566 MB written (fifo 100%) [buf  99%]  27.8x.
Track 01:   82 of  566 MB written (fifo 100%) [buf 100%]  26.9x.
Track 01:   83 of  566 MB written (fifo 100%) [buf 100%]  27.8x.
Track 01:   84 of  566 MB written (fifo  98%) [buf  99%]  27.0x.
Track 01:   85 of  566 MB written (fifo 100%) [buf 100%]  27.9x.
Track 01:   86 of  566 MB written (fifo  99%) [buf  93%]  27.1x.
Track 01:   87 of  566 MB written (fifo  99%) [buf  95%]  27.9x.
Track 01:   88 of  566 MB written (fifo  93%) [buf  99%]  27.1x.
Track 01:   89 of  566 MB written (fifo  98%) [buf  96%]  28.0x.
Track 01:   90 of  566 MB written (fifo 100%) [buf  97%]  27.2x.
Track 01:   91 of  566 MB written (fifo 100%) [buf  94%]  27.7x.
Track 01:   92 of  566 MB written (fifo 100%) [buf  97%]  27.5x.
Track 01:   93 of  566 MB written (fifo  99%) [buf  99%]  28.1x.
Track 01:   94 of  566 MB written (fifo 100%) [buf  99%]  27.3x.
Track 01:   95 of  566 MB written (fifo 100%) [buf  96%]  27.5x.
Track 01:   96 of  566 MB written (fifo  99%) [buf 100%]  29.8x.
Track 01:   97 of  566 MB written (fifo  99%) [buf 100%]  28.2x.
Track 01:   98 of  566 MB written (fifo  99%) [buf  99%]  29.1x.
Track 01:   99 of  566 MB written (fifo 100%) [buf 100%]  28.2x.
Track 01:  100 of  566 MB written (fifo 100%) [buf  99%]  29.2x.
Track 01:  101 of  566 MB written (fifo  99%) [buf  96%]  28.3x.
Track 01:  102 of  566 MB written (fifo  97%) [buf  99%]  29.2x.
Track 01:  103 of  566 MB written (fifo  97%) [buf  95%]  28.4x.
Track 01:  104 of  566 MB written (fifo  96%) [buf  99%]  29.3x.
Track 01:  105 of  566 MB written (fifo 100%) [buf  94%]  28.4x.
Track 01:  106 of  566 MB written (fifo 100%) [buf  85%]  26.1x.
Track 01:  107 of  566 MB written (fifo 100%) [buf  97%]  31.6x.
Track 01:  108 of  566 MB written (fifo  99%) [buf  94%]  30.0x.
Track 01:  109 of  566 MB written (fifo 100%) [buf 100%]  28.5x.
Track 01:  110 of  566 MB written (fifo  97%) [buf  99%]  29.4x.
Track 01:  111 of  566 MB written (fifo  99%) [buf  99%]  28.6x.
Track 01:  112 of  566 MB written (fifo 100%) [buf  98%]  29.2x.
Track 01:  113 of  566 MB written (fifo  99%) [buf  96%]  28.9x.
Track 01:  114 of  566 MB written (fifo 100%) [buf  99%]  29.5x.
Track 01:  115 of  566 MB written (fifo 100%) [buf  99%]  28.7x.
Track 01:  116 of  566 MB written (fifo  98%) [buf 100%]  29.6x.
Track 01:  117 of  566 MB written (fifo  93%) [buf  93%]  28.7x.
Track 01:  118 of  566 MB written (fifo 100%) [buf  97%]  29.7x.
Track 01:  119 of  566 MB written (fifo 100%) [buf  96%]  28.8x.
Track 01:  120 of  566 MB written (fifo 100%) [buf 100%]  29.7x.
Track 01:  121 of  566 MB written (fifo 100%) [buf  95%]  28.8x.
Track 01:  122 of  566 MB written (fifo  99%) [buf 100%]  29.8x.
Track 01:  123 of  566 MB written (fifo  95%) [buf  96%]  28.9x.
Track 01:  124 of  566 MB written (fifo  91%) [buf  99%]  29.8x.
Track 01:  125 of  566 MB written (fifo  94%) [buf  97%]  28.9x.
Track 01:  126 of  566 MB written (fifo  94%) [buf  99%]  29.8x.
Track 01:  127 of  566 MB written (fifo  90%) [buf 100%]  30.8x.
Track 01:  128 of  566 MB written (fifo  83%) [buf 100%]  29.8x.
Track 01:  129 of  566 MB written (fifo  79%) [buf  99%]  30.7x.
Track 01:  130 of  566 MB written (fifo  85%) [buf  99%]  30.1x.
Track 01:  131 of  566 MB written (fifo  94%) [buf  99%]  30.9x.
Track 01:  132 of  566 MB written (fifo  98%) [buf  97%]  29.8x.
Track 01:  133 of  566 MB written (fifo  97%) [buf  98%]  31.0x.
Track 01:  134 of  566 MB written (fifo  97%) [buf  99%]  30.0x.
Track 01:  135 of  566 MB written (fifo  99%) [buf  98%]  31.0x.
Track 01:  136 of  566 MB written (fifo 100%) [buf 100%]  30.0x.
Track 01:  137 of  566 MB written (fifo 100%) [buf  99%]  31.0x.
Track 01:  138 of  566 MB written (fifo  93%) [buf  92%]  30.1x.
Track 01:  139 of  566 MB written (fifo  97%) [buf 100%]  31.1x.
Track 01:  140 of  566 MB written (fifo  90%) [buf 100%]  30.1x.
Track 01:  141 of  566 MB written (fifo  97%) [buf  99%]  31.1x.
Track 01:  142 of  566 MB written (fifo  99%) [buf  98%]  29.9x.
Track 01:  143 of  566 MB written (fifo  99%) [buf 100%]  31.4x.
Track 01:  144 of  566 MB written (fifo 100%) [buf 100%]  30.2x.
Track 01:  145 of  566 MB written (fifo 100%) [buf  98%]  30.9x.
Track 01:  146 of  566 MB written (fifo  99%) [buf 100%]  30.5x.
Track 01:  147 of  566 MB written (fifo 100%) [buf  99%]  31.1x.
Track 01:  148 of  566 MB written (fifo 100%) [buf 100%]  30.4x.
Track 01:  149 of  566 MB written (fifo  99%) [buf 100%]  31.3x.
Track 01:  150 of  566 MB written (fifo  99%) [buf 100%]  30.3x.
Track 01:  151 of  566 MB written (fifo 100%) [buf 100%]  31.3x.
Track 01:  152 of  566 MB written (fifo 100%) [buf 100%]  30.4x.
Track 01:  153 of  566 MB written (fifo 100%) [buf  99%]  31.3x.
Track 01:  154 of  566 MB written (fifo 100%) [buf  95%]  30.4x.
Track 01:  155 of  566 MB written (fifo 100%) [buf  96%]  31.3x.
Track 01:  156 of  566 MB written (fifo  99%) [buf  99%]  30.5x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 01 38 2E 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F1 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (valid) 
cmd finished after 26.161s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 163672064 bytes
Writing  time:   89.097s
Average write speed  48.2x.
Min drive buffer fill was 85%
Fixating...
Fixating time:    0.003s
/usr/bin/wodim: fifo had 2770 puts and 2579 gets.
BURN-Free was 1 times used.
/usr/bin/wodim: fifo was 0 times empty and 1402 times full, min fill was 78%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=48 -dao driveropts=burnfree -overburn -data -tsize=289985s - 
```

Can anybody tell me what this means?

-pete

---

### Post by TeeAhr1 on 2007-10-27
Okay, turns out it's my drive.  I just had the problem with a different iso, but my external burner has no problem.  So where do I go from here in troubleshooting this?  Anybody?

-pete

---

### Post by MJN on 2007-10-27
Have you tried burning as root?

Mathew

---

### Post by disturbedite on 2007-10-27
i had a funny experience with this type of thing...
i ordered some more memory for my pc and installed it.
then i downloaded the kubuntu 7.10 dvd to do a fresh install on my pc.  i burned it, installed it but was having problems & getting errors booting.  when i could boot to kde & log in it would dump me back to the login screen after a short while.
so then i wasn't sure if it was my new ram or my new install of kubuntu that was the cause of the problems.  (although i knew the ram was not defective cuz i tested it by itself).

so i removed the new ram and reinstalled kubuntu with the same problems.  then i got the idea to check the disc for errors and sure enough there were 2 errors.  (it may have been due to the fact that i burned it @ 16x & forgot to burn it at a slower speed).

so then i re-downloaded kubuntu 7.10 but this time i just downloaded the cd version.  same problems all over again.  so i tested the disc and i couldn't believe there was another error!  (even though i burned it @ 8x, the slowest speed possible for my drive).  so i re-re-downloaded the disc and burned it, checked it for errors, & there weren't any & reinstalled.

problem solved.  but i also learned my new ram doesn't like to play well with my old ram, so i just left the new ram out.  (generates all kinds of errors if used in conjunction with my old ram but it works fine if i use it by itself.  but that defeats the purpose of why i bought it in the first place, since they're both 512MB modules).

i ordered some discs from shipit but i didn't wanna wait to get them and thats why i bothered downloading all those discs.

---

### Post by TeeAhr1 on 2007-10-29
> **MJN said:**
> Have you tried burning as root?

Mathew

It worked as root.  Something's seriously wrong here.  Sometimes (not always) it errors out when I try to eject, telling me I must be root.  I looked in the KDE settings and the drive is set to allow any one user at a time to mount/unmount.  Um...  ???

---

### Post by MJN on 2007-10-29
This sounds entirely normal to me. It's not so much the permissions on the mounting, but rather the ability to other things involved in burning. In particular, the warning in the debug info you posted specifically mentions it was unable to raise 'RLIMIT_MEMLOCK'. Now, whilst I don't know exactly what that is it sure sounds like something that would be nice to have, and raising if required, otherwise why would it want to?

I always burn as root as a matter of course. It also helps with locking the drive from any other (non-root) process that might start trying to stick its oar in e.g. auto-mount daemons and other 'helper' apps etc.

For ejecting, the drive obviously must be unmounted however unmounting requires that the file system is no longer in use. If it's still in use (e.g. you might have a terminal open and simply be 'sat' in one of its directories) then it won't unmount even by root unless you explicitly force it. Hence, a non-root user likely has no chance (or if it does it must also use the same force options).

The 'must be root' warning can sometimes be misleading - it's often given when something didn't work as expected (which may not have been due to you not being root). Next time you can't eject/unmount run **fuser -muv /media/cdrom **and this will tell you who/what is still 'using' the drive.

Mathew

---

