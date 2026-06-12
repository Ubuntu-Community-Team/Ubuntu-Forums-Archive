---
title: "K3B Hangs"
date: 2005-10-20
forum: General Help
---

### Post by Craig Prevallet on 2005-10-20
Hi, 

K3B hangs at the scanning for CD stage at the splash screen.  I then can kill the window/process.  

This a.m. after a reboot, K3b did manage to load and I burned a CD successfully.  However, it now hangs again.  I can also play audio CDs so I believe it is connected properly.  Problems appeared to begin for me after an upgrade about 3 days ago.

I'd appreciate some guidance.

System details follow from the successful burn:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /mnt/Mandrake10 ext3    defaults        0       2
/dev/hda8       /mnt/mandrake9  ext2    defaults        0       2
/dev/hda6       /mnt/oldhome    ext2    defaults        0       2
/dev/hda7       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0   

System
-----------------------
K3b Version: 0.12

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.12-9-386
Devices
-----------------------
5705-02E 59V1.500R23270MN  (/dev/hdc, ) at /media/cdrom1 [CD-ROM; DVD-ROM] [Error] [None]

PHILIPS CDD4801 CD-R/RW C1.3 (/dev/hdd, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM] [Error] [TAO; RAW; RAW/R16]
K3b
-----------------------
Size of filesystem calculated: 2568

Used versions
-----------------------
mkisofs: 2.1-unofficial-iconv
cdrecord: 2.1.1a01

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.12-9-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'PHILIPS '
Identifikation : 'CDD4801 CD-R/RW '
Revision       : 'C1.3'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO 
Supported modes: TAO PACKET RAW/R16
Drive buf size : 1572864 = 1536 KB
FIFO size      : 4194304 = 4096 KB
/usr/bin/X11/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/X11/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/X11/cdrecord: WARNING: This causes a high risk for buffer underruns.
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Track 01: data     5 MB        
Total size:        5 MB (00:34.26) = 2570 sectors
Lout start:        6 MB (00:36/20) = 2570 sectors
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
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 357279
Starting to write CD/DVD at speed 8 in real TAO mode for multi session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of    5 MB written.
Track 01:    1 of    5 MB written (fifo 100%) [buf  68%]  11.7x.
Track 01:    2 of    5 MB written (fifo 100%) [buf  99%]   2.5x.
Track 01:    3 of    5 MB written (fifo 100%) [buf  95%]   4.2x.
Track 01:    4 of    5 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:    5 of    5 MB written (fifo 100%) [buf  98%]   4.2x.
Track 01: Total bytes read/written: 5259264/5259264 (2568 sectors).
Writing  time:   21.897s
Average write speed   2.4x.
Min drive buffer fill was 95%
Fixating...
Fixating time:   64.624s
/usr/bin/X11/cdrecord: fifo had 83 puts and 83 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 10 times full, min fill was 96%.

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdd speed=8 -tao -eject -multi -xa -tsize=2568s - 

mkisofs
-----------------------
2568
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
 19.90% done, estimate finish Thu Oct 20 08:30:27 2005
 39.21% done, estimate finish Thu Oct 20 08:30:12 2005
 58.53% done, estimate finish Thu Oct 20 08:30:07 2005
 78.47% done, estimate finish Thu Oct 20 08:30:04 2005
Total translation table size: 0
Total rockridge attributes bytes: 253
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 21000
2568 extents written (5 MB)

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid DuckHunt v0.1.0 -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher Craig S. Prevallet -preparer Craig S. Prevallet -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-penguin/k3bBUjGPb.tmp -rational-rock -hide-list /tmp/kde-penguin/k3bhHO6ya.tmp -joliet -hide-joliet-list /tmp/kde-penguin/k3bpjkkFb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-penguin/k3bJ65rja.tmp

---

### Post by Craig Prevallet on 2005-10-20
Forgot to add the K3B version is 0.12.2-0ubuntu2.

---

### Post by Craig Prevallet on 2005-10-20
Hmmm...

Looks like this is being discussed elsewhere

[http://ubuntuforums.org/showthread.php?t=73855&highlight=cdrecord](http://ubuntuforums.org/showthread.php?t=73855&highlight=cdrecord)

---

### Post by Craig Prevallet on 2005-10-21
*bump* 

Anyone?

---

### Post by Craig Prevallet on 2005-10-21
I see this in Bugzilla:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=17373](http://bugzilla.ubuntu.com/show_bug.cgi?id=17373)

Looks like an issue with SCSI drivers and kernel 2.6.8 and above

---

### Post by Craig Prevallet on 2005-10-21
All right, no help from elsewhere--I'll tackle this myself.  

I've confirmed that the cd burner itself is O.K. by burning an ISO with cdrecord as root:

mkisofs -r -R -J -l -L -o /tmp/cd-iso-image-file.iso /home/penguin/Python/game_sixthversion

sudo cdrecord speed=2 /tmp/cd-iso-image-file.iso

It appears the problem is with k3b itself.

---

### Post by Craig Prevallet on 2005-10-21
Wow!

I attempted to start k3b again and just let it scan.  Eventually it came up after 3min and 15 seconds!  What's up?

---

