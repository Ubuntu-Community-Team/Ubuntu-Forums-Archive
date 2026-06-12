---
title: "[SOLVED] Disappearing DVD"
date: 2007-10-22
forum: General Help
---

### Post by starfry on 2007-10-22
Hi, I have a problem writing DVDs.

I've been reading DVDs for ages and it all works fine. I tried yesterday to write a DVD and it worked. "Great!, I thought, I'll write another one."

And that's where my problems begin...

I can quite happily put a DVD in my drive, read it and eject it

As soon as I put a blank DVD in the drive, however, the drive seems to die as far as Ubuntu is concerned. I can no longer see the drive and I can't eject it. The only way to get the blank disc out is to reboot.

After rebooting I can use the drive to read stuff.

Any ideas what is wrong?

Here are my device nodes:

% ls -l /dev/hd{c,d}*
brw-rw---- 1 root cdrom 22,  0 2007-10-22 23:27 /dev/hdc
brw-rw---- 1 root cdrom 22, 64 2007-10-22 23:27 /dev/hdd
% ls -l /dev/{cd,dvd}*
lrwxrwxrwx 1 root root 3 2007-10-22 23:27 /dev/cdrom -> hdd
lrwxrwxrwx 1 root root 3 2007-10-22 23:27 /dev/cdrw -> hdd
lrwxrwxrwx 1 root root 3 2007-10-22 23:27 /dev/dvd -> hdc
lrwxrwxrwx 1 root root 3 2007-10-22 23:27 /dev/dvdrw -> hdc

(this is on 7.04 Ubuntu Feisty)

---

### Post by starfry on 2007-10-28
HELP! I am still stuck with this. Here is some more information...  The drive in issue is the one on /dev/hdc which is  PIONEER DVD-RW DVR-104

sudo hdparm /dev/hdc                

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device


/usr/lib/nautilus-cd-burner/list_cddrives

** (process:5167): WARNING **: No property volume.disc.capacity on device with id /org/freedesktop/Hal/devices/volume_empty_unknown

Drive:
  name:                 Hewlett-Packard CD-Writer Plus 9300
  device:               /dev/hdd
  door:                 closed
  type:                 CD-R, CD-RW, CD
  is mounted:           FALSE
  max read speed:       5645 KiB/s (CD 37.6x, DVD 4.1x)
  max write speed:      1764 KiB/s (CD 11.7x, DVD 1.3x)
  write speeds:         1650 KiB/s (CD 11.0x, DVD 1.2x)
                        1500 KiB/s (CD 10.0x, DVD 1.1x)
                        1350 KiB/s (CD 9.0x, DVD 0.9x)
                        1200 KiB/s (CD 8.0x, DVD 0.8x)
                        1050 KiB/s (CD 7.0x, DVD 0.7x)
                        900 KiB/s (CD 6.0x, DVD 0.6x)
                        750 KiB/s (CD 5.0x, DVD 0.5x)
                        600 KiB/s (CD 4.0x, DVD 0.4x)
                        450 KiB/s (CD 3.0x, DVD 0.3x)
                        300 KiB/s (CD 2.0x, DVD 0.2x)
                        150 KiB/s (CD 1.0x, DVD 0.1x)

Media:
  label:                ''
  type:                 Couldn't open media
  is writable:          FALSE
  is appendable:        FALSE
  capacity:             Could not be determined
  size:                 Could not be determined
---
Drive:
  name:                 PIONEER DVD-RW DVR-104
  device:               /dev/hdc
  door:                 closed
  type:                 CD-R, CD-RW, DVD-R, DVD-RW, CD, DVD
  is mounted:           FALSE
  max read speed:       4233 KiB/s (CD 28.2x, DVD 3.1x)
  max write speed:      1411 KiB/s (CD 9.4x, DVD 1.0x)
  write speeds:         1411 KiB/s (CD 9.4x, DVD 1.0x)
                        705 KiB/s (CD 4.6x, DVD 0.5x)

Media:
  label:                ''
  type:                 Unknown Media (rewritable) (blank)
  is writable:          FALSE
  is appendable:        FALSE
  capacity:             Could not be determined
  size:                 0.00 MiB
---

cdrecord blank=fast dev=/dev/hdc         
Device type    : not present Object based storage
Version        : 0
Response Format: 10
Capabilities   : 
Device seems to be: unknown.
wodim: Sorry, no supported CD/DVD-Recorder found on this target.


If anyone can help with this, I'm stuck totally!

---

### Post by starfry on 2007-10-30
I discovered my XP had the same problem with the drive. I patched the firmware and that sorted it. Looks good so far...

For others info

Drive is Pioneer DVR-104 (also known as DVR-A04).
Original firmware version 1.20
Upgraded firmware version 1.31

---

