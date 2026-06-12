---
title: "Can't burn a DVD from an ISO with any of several tools"
date: 2007-11-07
forum: General Help
---

### Post by alanhoyle on 2007-11-07
I'm trying to burn a DVD ISO (Quantian:  a statistics-oriented Knoppix variant).  I've tried several burning tools:

I tried right-clicking the file.  gives the error > There was an error writing to the disc


I tried wodim.  it gives the following:  > $ sudo wodim -v Quantian_0.7.9.2.iso
Password:
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
Quickly guessing the name of a drive capable to write DVD-R, please wait...
Found /dev/dvdrw, assuming dev=/dev/dvdrw
TOC Type: 1 = CD-ROM
scsidev: '/dev/dvdrw'
devname: '/dev/dvdrw'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
Driveropts: 'burnfree'
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVD-RAM GSA-H30N'
Revision       : '1.06'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0011 (DVD-R sequential recording)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) (current)
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: 
Drive buf size : 1409024 = 1376 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Drive DMA Speed: 88372 kB/s 502x CD 63x DVD
FIFO size      : 4194304 = 4096 KB
Track 01: data  2726 MB        
Total size:     3130 MB (310:10.24) = 1395768 sectors
Lout start:     3131 MB (310:12/18) = 1395768 sectors
Current Secsize: 2048
  ATIP start of lead in:  -150 (00:00/00)
Disk type:    unknown dye (reserved id code)
Manuf. index: -1
Manufacturer: unknown (not in table)
wodim: Cannot init drive.
"There was an error writing to the disc"

I tried using k3m:  > Mediatype:       CD-ROM
Current Profile: No media
Disk state:      unknown
Empty:           0
Rewritable:      0
Appendable:      0
Sessions:        0
Tracks:          0
Layers:          1
Capacity:        00:00:01 (LBA 1) (2048 Bytes)
Remaining size:  00:00:00 (LBA 0) (0 Bytes)
Used Size:       00:00:01 (LBA 1) (2048 Bytes)
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
MediaManager::slotMediumAdded: scd1


I also tried xcdroast and growisofs, both to no avail.

Anyone have any suggestions?

---

### Post by markharding557 on 2007-11-07
check what your dvd drive is showing as in system menu/ device manager.
i have always known it to be /dev/hdc or /dev/hd( some letter),yours doesn't look right
if you don't see an entry like the above then the o/s is not seeing it
if it is then it probably isn't mounted
also something else could be locking your drive

---

### Post by alanhoyle on 2007-11-07
The device is /dev/scd1.  It's connected to a 2 port SATA IDE controller and the Device Manager seems to think it's a SCSI device.  Ubuntu mounts CDs and DVDs if I insert them into the dvd drive.

---

### Post by markharding557 on 2007-11-07
when you run a cd burning software you should see the device as /dev/scd1
also try running a burning app as root [gksu] this will tell you if it is a permissions problem

---

### Post by alanhoyle on 2007-11-07
I'd already tried running an "sudo wodim" before, but 

Here's the "debugging output" from gksu k3b:

> System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
ATAPI DVD D  DH16D1S GL31 (/dev/scd0, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]

HL-DT-ST DVD-RAM GSA-H30N 1.06 (/dev/scd1, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [TAO, Restricted Overwrite, Layer Jump]
Burned media
-----------------------
DVD-R Sequential

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd1 obs=32k seek=0'
:-[ MODE SELECT failed with SK=5h/ASC=1Ah/ACQ=00h]: Input/output error

growisofs command:
-----------------------
/usr/X11R6/bin/growisofs -Z /dev/scd1=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1395768 -dvd-compat -speed=16 -use-the-force-luke=bufsize:32m 


---

### Post by UK-Wobbie on 2007-11-07
> **alanhoyle said:**
> I'm trying to burn a DVD ISO (Quantian:  a statistics-oriented Knoppix variant).  I've tried several burning tools:

I tried right-clicking the file.  gives the error 


I tried wodim.  it gives the following:  

I tried using k3m:  

I also tried xcdroast and growisofs, both to no avail.

Anyone have any suggestions?

Is the ISO a DVD or CD ISO? :)
Some burning softwares can only burn CD ISOs.. And some will not yet you burn CD ISOs on to a DVD disk.
Only saying :)

---

### Post by TuxTwig on 2007-11-07
> **UK-Wobbie said:**
> Is the ISO a DVD or CD ISO? :)
Some burning softwares can only burn CD ISOs.. And some will not yet you burn CD ISOs on to a DVD disk.
Only saying :)

As others have said, double check the .iso file, it might be a CD .iso. Pretty much all modern burning software tools have DVD .iso burning properties.

---

### Post by alanhoyle on 2007-11-07
It's a DVD ISO.  I've burned a copy to DVD on another computer, just not my linux box.

[http://quantian.alioth.debian.org/](http://quantian.alioth.debian.org/)  

It's a Statistics-oriented Knoppix variant (2.7 GB DVD .ISO)  The MD5 sum passes fine.  

I've also tried burning a data DVD which also failed.  It's not something related to the source of the data to be burned, it's the target.

---

### Post by TuxTwig on 2007-11-07
So, the DVD .iso is fine, the media is ok, and your DVD drive is ok?

---

### Post by alanhoyle on 2007-11-07
the ISO is OK, the DVD drive can mount DVDs, and I've tried blank DVD+R and DVD-R media.  I suppose I could try burning a CD of some sort with a different ISO....

---

