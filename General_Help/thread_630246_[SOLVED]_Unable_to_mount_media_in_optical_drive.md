---
title: "[SOLVED] Unable to mount media in optical drive"
date: 2007-12-03
forum: General Help
---

### Post by The Pinny Parlour on 2007-12-03
Hi

I have an issue with media not mounting in the optical drive.  I can see the optical drive being detected, but no media.  I have used many different disc, (including Canonical Ubuntu discs).

Unable to mount media.  There is probably no media in the drive.

Any ideas?

Thanks,

---

### Post by The Pinny Parlour on 2007-12-04
Bump

---

### Post by geraldm on 2007-12-04
One way to check it out would be to use the BIOS, select it for booting, and then try to use a liveCD such as ubuntu.  You have such a disk from Canonical. ??
By optical drive, what hardware is it? CD,DVDROM
post the line in /etc/fstab that refers to the drive ?

Gerald

---

### Post by biocyberman on 2007-12-05
I am running Gusty Gibbon I386
This is line for my DVD +RW drive in fstab. 
```
/dev/scd0       /media/cdrom   udf,iso9660 user,noauto,exec 0       0
```

The drive worked flawlessly until I messed with:
1. System/Preferences/Removable Drives and Media
2. Unplug and Remove my DVD Drive (to bring to other PC) and plug in back again
3. Updates bunch of updates found by Update manager
I don't know what did cause the trouble. 

I still can mount the drive using: 
```
sudo mount /dev/scd0
```

Resulting mounted point is readonly. After that I can browse DVD/CD content from  /media/cdrom by nautilus but not by DVD icon in Places/Computer. In addition, even having been mounted, no DVD/CD icon appears on Desktop since the problem happens.

I also can write to DVD by using growisofs
```
sudo growisofs -speed=4 -dvd-compat -Z /dev/scd0=/path/to/isoimage.iso
```

Although I can do all the stuff but It is too geeky so I want to have automount back. I already check System/Administration/Users and Groups permission but no use :mad:

---

### Post by The Pinny Parlour on 2007-12-07
BUMP

DVD drive

---

### Post by The Pinny Parlour on 2007-12-10
Bump

---

### Post by The Pinny Parlour on 2007-12-14
Bump

---

### Post by kpkeerthi on 2007-12-14
... deleted wrong post ...

---

### Post by The Pinny Parlour on 2007-12-16
I now know what may have caused the issue.  I recently changed the optical drive.  Anyone know how to fix this?  It's on Secondary Master.

---

### Post by The Pinny Parlour on 2008-01-01
BUMP

It can't possibly be that hard to get this working can it?

Background:   Changed optical drives.   How can I get this to see any media inserted into the optical drive?

---

### Post by The Pinny Parlour on 2008-01-04
Finally SOLVED.

I person I know asked me to type the following into terminal with a disc in the drive:

```

sudo mkdir /mnt/testcd
sudo mount /dev/scd0 -t iso9660 /mnt/testcd
sudo ls /mnt/testcd/
```

the output was:
XXX@XXX-desktop:~$ sudo mkdir /mnt/testcd
[sudo] password
XXX@XXX-desktop:~$ sudo mkdir /mnt/testcd
mkdir: cannot create directory `/mnt/testcd': File exists
XXX@XXX-desktop:~$ sudo mount /dev/scd0 -t iso9660 /mnt/testcd
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
XXX@XXX-desktop:~$ sudo ls /mnt/testcd/


```

sudo ls -lah /dev/scd0
sudo dmesg | tail -n 20
```

Output was:
XXX@XXX-desktop:~$ sudo ls -lah /dev/scd0
[sudo] password
brw-rw---- 1 root cdrom 11, 0 2008-01-02 10:24 /dev/scd0
XXX@XXX-desktop:~$ sudo dmesg | tail -n 20
[ 42.751629] eth0: no IPv6 routers present
[ 607.624948] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 607.624962] ata2.00: cmd a0/00:00:00:00:20/00:00:00:00:00/a0 tag 0 cdb 0x0 data 0
[ 607.624964] res 51/20:03:00:00:20/00:00:00:00:00/a0 Emask 0x1 (device error)
[ 607.779467] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x1)
[ 607.779475] ata2.00: revalidation failed (errno=-5)
[ 607.779482] ata2: failed to recover some devices, retrying in 5 secs
[ 612.774585] ata2: soft resetting port
[ 613.086133] ata2.00: revalidation failed (errno=-2)
[ 613.086143] ata2: failed to recover some devices, retrying in 5 secs
[ 618.081364] ata2: soft resetting port
[ 618.392918] ata2.00: revalidation failed (errno=-2)
[ 618.392927] ata2.00: disabled
[ 618.895959] ata2: EH complete
[19649.509620] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[27702.570641] usb 3-5: new high speed USB device using ehci_hcd and address 2
[27702.704658] usb 3-5: configuration #1 chosen from 1 choice
[27702.878494] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04A9 pid 0x10B6
[27702.878940] usbcore: registered new interface driver usblp
[27702.879123] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver

Those errors are to do with your IDE ports, not the drive itself. The issue is lower level than the drive.

Your IDE controller on the motherboard is stuffed (or you've got a bad cable). Try moving it to another port (ie: it's on ATA2 at the moment (Secondary IDE), try moving it to ATA1 (Primary IDE) if you can. Try a new cable too".

Inspection of IDE cable showed it was indeed faulty, (pulled on a little to much over time).  Replaced and all works.
From this he told me: "

---

