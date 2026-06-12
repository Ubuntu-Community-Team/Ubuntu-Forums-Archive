---
title: "Gnomebaker, Nautilus-burner, and cdrecord"
date: 2005-04-09
forum: General Help
---

### Post by audax321 on 2005-04-09
i've been trying to burn an iso but i get the following output from cdrecord and then a it just sits there:

```

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-5-686-smp
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'CENDYNE_'
Identifikation : '481648AX        '
Revision       : '150F'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R

```

I tried Gnomebaker and Nautilus-burner and both gave the same results since they just use cdrecord to burn anyway. Does anybody know why or how to correct this?  ](*,)

---

### Post by audax321 on 2005-04-09
anyone? i really need to be able to burn cds... is there something wrong with the cdrecord package?

Maybe this will help:

I get an error message with Gnomebaker saying that it can't mount /dev/hdc to /media/cdrom1. So I tried to manually mount it and got this:

> 
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I have not edited any of the cdrom entries in fstab so I'm assuming that maybe Ubuntu put it in wrong, this is the cd-recorder's line:

> 
/dev/hdc        /media/cdrom1   udf,iso9660    ro,user,noauto  0       0
 

Does anyone know if there is something wrong with this?

---

### Post by kleeman on 2005-04-09
I have had a LOT of problems with cdrecord in hoary. What does
sudo cdrecord -scanbus

show?

What is in 

/etc/default/cdrecord

---

### Post by audax321 on 2005-04-09
sudo cdrecord -scanbus gives me this:

```

Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-5-686-smp
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup 

``` 

And this is /etc/default/cdrecord:

```

#ident @(#)cdrecord.dfl	1.4 02/07/07 Copyr 1998 J. Schilling
#
# This file is /etc/default/cdrecord
# It contains defaults that are used if no command line option
# or environment is present.
# 
# The default device, if not specified elswhere
#
CDR_DEVICE=yamaha

# 
# The default speed, if not specified elswhere
#
# Note that newer cdrecord versions do not default
# to speed=1. For MMC compliant drives, the default
# is to write at maximum speed, so it in general does
# not make sense to set up a default speed in /etc/default/cdrecord 
#
#CDR_SPEED=40

# 
# The default FIFO size if, not specified elswhere
#
CDR_FIFOSIZE=4m

#
# The following definitions allow abstract device names.
# They are used if the device name does not contain the
# the characters ',', ':', '/' and '@'
#
# Unless you have a good reason, use speed == -1 and let
# cdrecord use it's intercal drive specific defaults.
#
# drive name	device	speed	fifosize driveropts
#
teac=		1,3,0	-1	-1	""
panasonic=	1,4,0	-1	-1	""
plextor=	1,4,0	-1	-1	""
sanyo=		1,4,0	-1	-1	burnfree
yamaha=		1,5,0	-1	-1	""
cdrom=		0,6,0	2	1m	""

```

---

### Post by kleeman on 2005-04-10
That sounds severe. What does
sudo cdrecord dev=/dev/hdc -scanbus 
show?
Also I assume you have an ide rather than scsi cd writer.

---

### Post by audax321 on 2005-04-10
thanks for your help. that command gives me this:

```

Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-5-686-smp
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus1:
        1,0,0   100) 'CENDYNE_' '481648AX        ' '150F' Removable CD-ROM
        1,1,0   101) *
        1,2,0   102) *
        1,3,0   103) *
        1,4,0   104) *
        1,5,0   105) *
        1,6,0   106) *
        1,7,0   107) *

```

And yes, it is an IDE drive. I've used it under other distros, and its worked, so not sure what is going on here...

---

### Post by kleeman on 2005-04-10
OK at least scanbus is working. In your config file /etc/default/cdrecord it is assuming a yamaha drive (not important) and assuming it is at 1,5,0 (important) Change this to the value revealed by scanbus i.e. 1,0,0 and see if things improve.

---

### Post by audax321 on 2005-04-10
okay, this is what is happening now:

```

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-5-686-smp
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'CENDYNE_'
Identifikation : '481648AX        '
Revision       : '150F'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
resid: 64508
resid: 64508
cdrecord: Success. read buffer: scsi sendcmd: no error
CDB:  3C 00 00 00 00 00 00 FC 00 00
status: 0xb (Reserved)
Sense Bytes:
Sense Key: 0xFFFFFFFF [], Segment 0
Sense Code: 0x00 Qual 0x00 (no additional sense information) Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 64512
cmd finished after 85.195s timeout 40s

```

then it just sits there after that...

---

### Post by Jad on 2005-04-10
I have same problem
**here is my /etc/default/cdrecord**

```
#ident @(#)cdrecord.dfl	1.4 02/07/07 Copyr 1998 J. Schilling
#
# This file is /etc/default/cdrecord
# It contains defaults that are used if no command line option
# or environment is present.
# 
# The default device, if not specified elswhere
#
CDR_DEVICE=yamaha

# 
# The default speed, if not specified elswhere
#
# Note that newer cdrecord versions do not default
# to speed=1. For MMC compliant drives, the default
# is to write at maximum speed, so it in general does
# not make sense to set up a default speed in /etc/default/cdrecord 
#
#CDR_SPEED=40

# 
# The default FIFO size if, not specified elswhere
#
CDR_FIFOSIZE=4m

#
# The following definitions allow abstract device names.
# They are used if the device name does not contain the
# the characters ',', ':', '/' and '@'
#
# Unless you have a good reason, use speed == -1 and let
# cdrecord use it's intercal drive specific defaults.
#
# drive name	device	speed	fifosize driveropts
#
teac=		1,3,0	-1	-1	""
panasonic=	1,4,0	-1	-1	""
plextor=	1,4,0	-1	-1	""
sanyo=		1,4,0	-1	-1	burnfree
yamaha=		1,5,0	-1	-1	""
cdrom=		0,6,0	2	1m	""

```
also assumed as Yamaha ( Why yamaha ?)

**and Here is my scanBus result**

```
jad@ubuntu:~ $ sudo cdrecord dev=/dev/hdc -scanbus
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus1:
        1,0,0   100) 'AOPEN   ' 'CD-RW CRW5224   ' '1.05' Removable CD-ROM
        1,1,0   101) *
        1,2,0   102) *
        1,3,0   103) *
        1,4,0   104) *
        1,5,0   105) *
        1,6,0   106) *
        1,7,0   107) *
```

---

### Post by Jad on 2005-04-10
ok edit my /etc/default/cdrecord
to 
```
CDR_DEVICE=AOPEN
```
And
```

teac=		1,3,0	-1	-1	""
panasonic=	1,4,0	-1	-1	""
plextor=	1,4,0	-1	-1	""
sanyo=		1,4,0	-1	-1	burnfree
#yamaha=	1,5,0	-1	-1	""
AOPEN=		1,0,0	-1	-1	""
cdrom=		0,6,0	2	1m	""
```

as the result from scanbus was
```
1,0,0   100) 'AOPEN   ' 'CD-RW CRW5224   ' '1.05' Removable CD-ROM
```

I'll test it now and report.

---

### Post by Jad on 2005-04-10
just rebooted and tried to burn a cd and faild.

---

### Post by Jad on 2005-04-10
One more error by gnome baker```

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'AOPEN   '
Identifikation : 'CD-RW CRW5224   '
Revision       : '1.05'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009
Profile: 0x0008
Profile: 0x0009 (current)
Profile: 0x000A
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
Drive buf size : 1359872 = 1328 KB
FIFO size      : 4194304 = 4096 KB
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
Track 01: data   679 MB       
Total size:      780 MB (77:18.44) = 347883 sectors
Lout start:      780 MB (77:20/33) = 347883 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11834 (97:24/16)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 24
Manufacturer: SONY Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 11966
Forcespeed is OFF.
Starting to write CD/DVD at speed 12 in real TAO mode for multi session.
Last chance to quit, starting real write in 2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Performing OPC...
Starting new track at sector: 0

Track 01:    0 of  679 MB written.
Track 01:    1 of  679 MB written (fifo  96%) [buf  80%] 103.1x.
Track 01:    2 of  679 MB written (fifo 100%) [buf 100%]   6.3x.
Track 01:    3 of  679 MB written (fifo 100%) [buf 100%]  12.7x.
Track 01:    4 of  679 MB written (fifo 100%) [buf 100%]  12.3x.
Track 01:    5 of  679 MB written (fifo 100%) [buf 100%]  12.7x.
Track 01:    6 of  679 MB written (fifo 100%) [buf 100%]  12.3x.
Track 01:    7 of  679 MB written (fifo 100%) [buf 100%]  12.7x.
Track 01:    8 of  679 MB written (fifo 100%) [buf 100%]  12.3x.
Track 01:    9 of  679 MB written (fifo 100%) [buf 100%]  12.7x.
Track 01:   10 of  679 MB written (fifo 100%) [buf 100%]  12.3x.
Track 01:   11 of  679 MB written (fifo 100%) [buf 100%]  12.7x.
Track 01:   12 of  679 MB written (fifo 100%) [buf 100%]  12.2x.
Track 01:   13 of  679 MB written (fifo 100%) [buf 100%]  12.6x.
Track 01:   14 of  679 MB written (fifo 100%) [buf 100%]  12.2x.
Track 01:   15 of  679 MB written (fifo 100%) [buf 100%]  12.6x.
Track 01:   16 of  679 MB written (fifo 100%) [buf 100%]  12.2x.
Track 01:   17 of  679 MB written (fifo 100%) [buf 100%]  12.6x.
Track 01:   18 of  679 MB written (fifo 100%) [buf 100%]  12.2x.
Track 01:   19 of  679 MB written (fifo 100%) [buf 100%]  12.6x.
Track 01:   20 of  679 MB written (fifo 100%) [buf 100%]  12.2x.
Track 01:   21 of  679 MB written (fifo 100%) [buf 100%]  12.5x.
Track 01:   22 of  679 MB written (fifo 100%) [buf 100%]  12.1x.
Track 01:   23 of  679 MB written (fifo  92%) [buf  91%]  11.3x.
Track 01:   24 of  679 MB written (fifo 100%)   4.7x.cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 30 13 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 05 00 00 30 15 0C 00 00 00 00 10 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x10 Qual 0x02 (id crc or ecc error) [No matching qualifier] Fru 0x0
Sense flags: Blk 12309 (valid)
resid: 63488
cmd finished after 0.005s timeout 40s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

write track data: error after 25204736 bytes
Writing  time:   30.309s
Average write speed 224.8x.
Min drive buffer fill was 91%
Fixating...
Fixating time:   21.907s
cdrecord: fifo had 461 puts and 398 gets.
cdrecord: fifo was 0 times empty and 364 times full, min fill was 87%.
```

I have tried to run it as root but got same errors.

---

### Post by kleeman on 2005-04-10
OK so now it looks like cdrecord is at least trying to do something ;-) I have occasional failures now and they are usually accompanied by rather nasty looking dmesg messages. What do you see if you execute dmesg after your cdrecord? I use the following command to burn isos:
cdrecord -dao -v -data *.iso
does this work?
Also what happens with nautilus cd-writer- this has been fairly reliable for me
If you still can't get this working I suggest you both lodge a bug report in the ubuntu bugzilla. The devs need to see that cd writing is not great at present...

---

### Post by audax321 on 2005-04-10
I tried your command but no luck. This is the relevant output from dmesg:

```

attempt to access beyond end of device
hdc: rw=0, want=68, limit=4
attempt to access beyond end of device
hdc: rw=0, want=1252, limit=4
attempt to access beyond end of device
hdc: rw=0, want=1028, limit=4
UDF-fs: No partition found (1)
attempt to access beyond end of device
hdc: rw=0, want=68, limit=4
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
hdc: status error: error=0x00
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: ATAPI reset complete
hdc: status error: status=0x08 { DataRequest }
hdc: status error: error=0x01IllegalLengthIndication
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: ATAPI reset complete
hdc: status error: status=0x08 { DataRequest }
hdc: status error: error=0x01IllegalLengthIndication
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: ATAPI reset complete
hdc: status error: status=0x08 { DataRequest }
hdc: status error: error=0x01IllegalLengthIndication
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: ATAPI reset complete
hdc: status error: status=0x08 { DataRequest }
hdc: status error: error=0x01IllegalLengthIndication
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: ATAPI reset complete
hdc: status error: status=0x08 { DataRequest }
hdc: status error: error=0x01IllegalLengthIndication
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: ATAPI reset complete
hdc: status error: status=0x08 { DataRequest }
hdc: status error: error=0x01IllegalLengthIndication
hdc: drive not ready for command
hdc: status timeout: status=0xd0 { Busy }
hdc: status timeout: error=0xd0LastFailedSense 0x0d
hdc: drive not ready for command
hdc: ATAPI reset complete
hdc: request sense failure: status=0x51 { DriveReady SeekComplete Error }
hdc: request sense failure: error=0x50LastFailedSense 0x05
hdc: request sense failure: status=0x51 { DriveReady SeekComplete Error }
hdc: request sense failure: error=0x50LastFailedSense 0x05

``` 

I'll file a bug report later, hopefully they can release an update to hoary and get this fixed instead of waiting six months..

---

### Post by kleeman on 2005-04-10
Hear! Hear! these things are quite annoying. If you hear back from the devs please add the info to this thread.

---

### Post by audax321 on 2005-04-10
Okay, bugs posted here:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8908](https://bugzilla.ubuntu.com/show_bug.cgi?id=8908)

Hopefully they can figure something out   :-?

---

### Post by RastaMahata on 2005-04-10
well, I get a "unable to mount /media/cdrom0" :(
I just cant burn cds after an upgrade to hoary! :@

edit: Well, it still gives me that message box when I tell it to "bake" me a cd, but it does bake the cd at the end... I dont know why this message keeps popping up though :/

---

### Post by qiet72 on 2006-01-19
Try adding "-ts=32768" parameter to cdrecord.  This is a known bug at least on LG burners.

Quinn

[QUOTE=audax321]okay, this is what is happening now:

```

Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
resid: 64508
resid: 64508
cdrecord: Success. read buffer: scsi sendcmd: no error
CDB:  3C 00 00 00 00 00 00 FC 00 00
status: 0xb (Reserved)
Sense Bytes:
Sense Key: 0xFFFFFFFF [], Segment 0
Sense Code: 0x00 Qual 0x00 (no additional sense information) Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 64512
cmd finished after 85.195s timeout 40s

```

then it just sits there after that...[/QUOTE]

---

