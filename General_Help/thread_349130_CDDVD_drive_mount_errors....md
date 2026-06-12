---
title: "CD/DVD drive mount errors..."
date: 2007-01-29
forum: General Help
---

### Post by Culito on 2007-01-29
I can play cd's just fine, but when I've tried to rip a few songs off of some cd's I have, I get an error in Sound Juicer:
Invalid Paramaters.
Also, I can't see the drive's contents in any program except for Sound Juicer...

I did a quick dmesg | tail and got this:

[11449.749300] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[11449.749329] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[11449.749339] ide: failed opcode was: unknown
[11449.749351] end_request: I/O error, dev hdc, sector 64
[11449.749915] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

The fstab line for the drive is:

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto 0 0

It doesn't matter what cd I put in.  Same error.  Any ideas?

---

### Post by mayonaise15 on 2007-01-29
My bet would be that either your drive or the IDE cable connecting it is dying.  Do you have another drive/cable that you could swap in?

---

