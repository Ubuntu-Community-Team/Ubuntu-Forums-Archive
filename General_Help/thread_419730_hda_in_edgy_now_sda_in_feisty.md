---
title: "hda in edgy now sda in feisty?"
date: 2007-04-23
forum: General Help
---

### Post by moore.bryan on 2007-04-23
[I]generic question, but didn't know where else to put it...

my ide harddrive went from /dev/hda to /dev/sda when i installed feisty; my hd isn't scsi/sata/usb.  huh?
[/I]

---

### Post by mcduck on 2007-04-23
Developers found out that SATA/SCSI drivers handle PATA drives better than the PATA driver did, so they started using them for all disks. No need to worry about that. :)

---

### Post by moore.bryan on 2007-04-23
*thanks for the reply, mcduck, but what about the fact my hd isn't sata/scsi?*

---

### Post by rich.bradshaw on 2007-04-23
It doesn' matter. The sata drivers work better, so are used for everything now.

---

### Post by moore.bryan on 2007-04-23
*ah, i see.  many thanks.*

---

### Post by Rescue9 on 2007-05-11
yea... but unfortunately the PATA drives don't hotplug with scsiadd or hotplug now.

---

### Post by sofTest on 2007-05-17
> **mcduck said:**
> Developers found out that SATA/SCSI drivers handle PATA drives better than the PATA driver did, so they started using them for all disks. No need to worry about that. :)

Well, I do worry a bit, because my HDD SMART doesn't work any more.  Do you know if this also is deliberately, or should I log it as a bug? Thanks.

Edit: Found a solution.  Had to use the option for device type.  Ie: sudo smartctl -d ata -a /dev/sda

---

### Post by manifoldronin on 2007-05-23
> **sofTest said:**
> Well, I do worry a bit, because my HDD SMART doesn't work any more.  Do you know if this also is deliberately, or should I log it as a bug? Thanks.

Edit: Found a solution.  Had to use the option for device type.  Ie: sudo smartctl -d ata -a /dev/sda

I am having something weird going with my ide dvd drive, too. See [this thread]("http://ubuntuforums.org/showthread.php?p=2691254").  I wonder if anyone else has had the similar problems.

---

### Post by simpsonsfan74 on 2007-05-25
I, too am worried about the switch from PATA drivers in Edgy to SCSI/SATA drivers in Feisty.  I can't turn DMA on for my CD drive (/dev/cdrom is now a symlink to /dev/scd0 instead of /dev/hdc).
sudo hdparm /dev/scd0 gives me:

/dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

and sudo hdparm -d1 /dev/scd0 gives me:

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

Can I turn on DMA any other way other than this method, [ found here?]("https://help.ubuntu.com/community/DMA")

Are there any other side-effects of the switch?

Can I revert back to the PATA drivers?

Thanks!

---

### Post by rjtd on 2007-07-01
We want the option to revert to the "older and worst" PATA driver!

---

