---
title: "CD burning problems"
date: 2007-02-02
forum: General Help
---

### Post by nibsa1242 on 2007-02-02
Hello. I am having problems burning to -R cd recording media in using Edgy. The results of my latest coaster are below, I used Gnomebaker. I have no problem burning to -RW media. Nor do I have a problem with +/- RW DVDs. Occasionally I make toasters with -R DVDs, but only about 10% of the time. I was burning at 6x for the below. 

```

cdrecord: Warning: Running on Linux-2.6.17-10-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c   1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 0 = CD-DA
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : 'PHILIPS '
Identifikation : 'DVD+-RW SDVD8441'
Revision       : 'PA48'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x002B
Profile: 0x001B
Profile: 0x001A
Profile: 0x0014
Profile: 0x0013
Profile: 0x0011
Profile: 0x0010
Profile: 0x000A
Profile: 0x0009 (current)
Profile: 0x0008
Profile: 0x0000
Profile: 0x0000
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1073152 = 1048 KB
FIFO size      : 4194304 = 4096 KB
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
Sending CUE sheet...
cdrecord: Success. read track info: scsi sendcmd: no error
CDB:  52 01 00 00 00 FF 00 00 1C 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 28
cmd finished after 0.001s timeout 240s
cdrecord: Cannot get next writable address for 'invisible' track.
cdrecord: This means that we are checking recorded media.
cdrecord: This media cannot be written in streaming mode anymore.
cdrecord: If you like to write to 'preformatted' RW media, try to blank the media first.
SAO startsec: -11839
Writing lead-in...
Lead-in write time:   27.648s
Writing pregap for track 1 at -150
Starting new track at sector: 0
cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 02 B0 93 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 63504
cmd finished after 7.212s timeout 200s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

write track data: error after 22607424 bytes
Writing  time:  334.923s
Average write speed  15.3x.
Min drive buffer fill was 87%
Fixating...
Fixating time:    0.003s
cdrecord: fifo had 6597 puts and 6534 gets.
cdrecord: fifo was 0 times empty and 4064 times full, min fill was 92%. 

```

---

### Post by r4ik on 2007-02-02
Install K3b it is in Synaptic, the better burning software i.m.o

---

### Post by theslut on 2007-02-02
> **r4ik said:**
> Install K3b it is in Synaptic, the better burning software i.m.o


don't they use all the same libraries?

I tend to use Nero Linux (horrible interface) but for my burner it burns faster and better than the native linux apps like k3b and brasero (unfortuately).

---

### Post by _simon_ on 2007-02-02
Try k3b and burn using TAO, pretty sure it will burn without issue.

---

### Post by BjarneJ on 2007-02-04
How do you go about specifying that K3B uses TAO when burning?

---

### Post by nicnocquee on 2007-02-07
please heeeeelp, i tried to burn data to cd using nautilus, it said successful, but i can't read the data from the cd. then i tried using gnomebaker, it always failed -> cdrecord: OPC failed. then i tried using k3b, wrote successfully, but the cd again couldn't be read. i tried to read it on different computers, but no luck. my cd writer is PHILIPS CDRW/DVD. why is it so hard to burn cd on Ubuntu?:(

---

### Post by nibsa1242 on 2007-02-07
k3b fails as well. The only reason that I've tried gnomebaker and brassero is because it wouldn't work in k3b

---

### Post by david_2001 on 2007-02-07
Please try an Internet search for "SDVD8441", i.e. the model of your DVD drive as reported by cdrecord.  It seems that a lot of people have had problems with this particular drive.  For example, take a look at [this thread]("http://www.averatecforums.com/archive/index.php/t-3813.html") and [this thread]("http://forums.afterdawn.com/thread_view.cfm/320544") (which has a possible solution at the end).

---

