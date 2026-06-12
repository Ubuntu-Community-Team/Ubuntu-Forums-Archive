---
title: "USB stick stuck as read-only"
date: 2013-09-09
forum: General Help
---

### Post by nick34 on 2013-09-09
Hi,

I have an 8gig Sandisk USB stick that is stuck in read-only mode. There is no write-protect switch on the drive. I'm not able to mount the drive and I'm not able to reformat it with gparted. Gparted just gives me another read-only error.  When I right-click to view permissions in my file manager it just says permissions could not be determined.

dmesg | tail output:
```

[153161.744410] scsi 10:0:0:0: Direct-Access     SanDisk  Cruzer           1.20 PQ: 0 ANSI: 5
[153161.745125] sd 10:0:0:0: Attached scsi generic sg3 type 0
[153161.749616] sd 10:0:0:0: [sdc] 15633408 512-byte logical blocks: (8.00 GB/7.45 GiB)
[153161.751486] sd 10:0:0:0: [sdc] Write Protect is on
[153161.751490] sd 10:0:0:0: [sdc] Mode Sense: 43 00 80 00
[153161.752587] sd 10:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[153161.762765]  sdc: sdc1
[153161.766937] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[153161.978139] EXT4-fs (sdc1): INFO: recovery required on readonly filesystem
[153161.978142] EXT4-fs (sdc1): write access unavailable, cannot proceed

```

I'm not sure how it got set to read-only and I'm not sure what else to try. Any help is appreciated. 

Thanks!

---

### Post by westie457 on 2013-09-09
What file system is on the drive please? Is it ext4, ntfs or fat32?

Ignore the above. You edited your post as I was writing mine.

You need to force a fsck on the device. See 'man fsck' in a terminal for ideas and usage.

---

### Post by nick34 on 2013-09-09
When I try to use fsck it tells me that it is write protected. Again though, there is no write protection switch. 

sudo fsck.ext4 /dev/sdc1
```

fsck.ext4: Read-only file system while trying to open /dev/sdc1
Disk write-protected; use the -n option to do a read-only
check of the device.

```

sudo fsck.ext4 -n /dev/sdc1
```

e2fsck 1.42.5 (29-Jul-2012)
Warning: skipping journal recovery because doing a read-only filesystem check.
/dev/sdc1: clean, 11/488640 files, 67745/1954172 blocks

```

After searching the forums more, a lot people seem to be having trouble with this device (Sandisk Cruzer 8gb). The only thing that seems to have worked for anyone is formatting it under another OS like Windows, but I don't have easy access to any OS besides Linux. Plus I don't want this to just happen again. I won't buy another Sandisk drive, but it's the only USB stick I have right now and I would like for it to work.

---

### Post by ant2 on 2013-09-09
Have you tried to format it using gparted that is booted from a CD

[gparted live](http://gparted.sourceforge.net/livecd.php)

---

### Post by nick34 on 2013-09-09
> **ant2 said:**
> Have you tried to format it using gparted that is booted from a CD

[gparted live]("http://gparted.sourceforge.net/livecd.php")

No, I don't have any blank CDs right now but that is something I can try as soon as I do.

---

### Post by GreatDanton on 2013-09-09
You don't need blank cd as you can boot it from usb, but oh well I forgot you got only 1 usb.
Also if you happen to have Cd with Ubuntu on it, there should be gparted on it.

---

