---
title: "Gnomebaker Error &amp; Speed"
date: 2006-12-09
forum: General Help
---

### Post by ahaslam on 2006-12-09
I've had problems with Gnomebaker (0.6.0 backports) before but not quite like this.

Firstly I had the old permissions error which I easily solved with: sudo chmod +s /usr/bin/gnomebaker

Now I seem to have a speed related issue with gnomebaker alone. I keep trying to burn an iso to a cd-rw, & it seems to be going for some kind of speed record. My drive is a 24 speed, the disk is a 12 speed and it's trying to burn at x40! Unsurprisingly it's resulting in a failed burn, what's going on?

If I simply right-click on an iso to burn it works perfectly, as does k3b.

I've included the output for further info:

```
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-27-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identifikation : 'UJ-840D         '
Revision       : '1.00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0013 
Profile: 0x0014 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A (current)
Profile: 0x0009 
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO
Drive buf size : 1310720 = 1280 KB
FIFO size      : 4194304 = 4096 KB
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Performing OPC...
Starting new track at sector: 0
cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 01 2C 12 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 71 00 05 00 00 00 00 0A 00 00 00 00 21 02 00 00
Sense Key: 0x5 Illegal Request, deferred error, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.003s timeout 40s
cdrecord: The current problem looks like a buffer underrun.
cdrecord: Try to use 'driveropts=burnfree'.
cdrecord: Make sure that you are root, enable DMA and check your HW/OS set up.

write track data: error after 157323264 bytes
Writing  time:  119.912s
Average write speed  39.0x.
Min drive buffer fill was 27%
Fixating...
Fixating time:   34.574s
cdrecord: fifo had 2542 puts and 2479 gets.
cdrecord: fifo was 4 times empty and 2321 times full, min fill was 0%.
```

As always, any comments or suggestions would be greatly appreciated ;)

Tony.

---

### Post by ahaslam on 2006-12-09
OK, as backports has messed up a few things for me, I've reverted back to GnomeBaker 0.5.1 (Dapper). After changing the permissions (again - what is it with this?), I attempted the same iso on the same cd-rw. It failed again and it's still trying to write too fast. I have explicitly set the write speed, but it takes little notice. There is a small improvement, it's going for x18 instead of x40 :rolleyes: - here's the output:

```
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-27-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identifikation : 'UJ-840D         '
Revision       : '1.00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0013 
Profile: 0x0014 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A (current)
Profile: 0x0009 
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO
Drive buf size : 1310720 = 1280 KB
FIFO size      : 4194304 = 4096 KB
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Turning BURN-Free off
Performing OPC...
Starting new track at sector: 0
cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 02 93 F6 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 71 00 05 00 00 00 00 0A 00 00 00 00 21 02 00 00
Sense Key: 0x5 Illegal Request, deferred error, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.003s timeout 40s
cdrecord: The current problem looks like a buffer underrun.
cdrecord: Try to use 'driveropts=burnfree'.
cdrecord: Make sure that you are root, enable DMA and check your HW/OS set up.

write track data: error after 346009600 bytes
Writing  time:  236.015s
Average write speed  18.4x.
Min drive buffer fill was 97%
Fixating...
Fixating time:   35.727s
cdrecord: fifo had 5514 puts and 5451 gets.
cdrecord: fifo was 2 times empty and 5042 times full, min fill was 0%.

```

I've just noticed something that I missed before, "Make sure that you are root, enable DMA and check your HW/OS set up". Surely having done **sudo chmod +s /usr/bin/gnomebaker**, permissions should be ok & I'm sure that DMA is on, but what's the 'HW/OS set up' bit referring to? 

Please advise, I'm tearing my hair out here ](*,) 

Tony.

---

### Post by ahaslam on 2006-12-10
**FIXED :)**

DMA was on:
```
ahaslam@ahaslam-laptop:~$ hdparm /dev/hdc

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
```

It required the following:
```

sudo chmod +s /usr/bin/gnomebaker 
sudo chmod +s /usr/bin/cdrecord
```

It's now burning at a modest but reliable speed with no errors:
```
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-27-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identifikation : 'UJ-840D         '
Revision       : '1.00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0013 
Profile: 0x0014 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A (current)
Profile: 0x0009 
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO
Drive buf size : 1310720 = 1280 KB
FIFO size      : 4194304 = 4096 KB
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Turning BURN-Free off
Performing OPC...
Starting new track at sector: 0
Writing  time:  433.177s
Average write speed   9.9x.
Min drive buffer fill was 93%
Fixating...
Fixating time:   37.169s
cdrecord: fifo had 10274 puts and 10274 gets.
cdrecord: fifo was 5 times empty and 9006 times full, min fill was 0%.
```

I find it strange how this only applied to Gnomebaker - I could make data/audio cd's with k3b & burn iso's with the right-click option.

Tony;)

---

