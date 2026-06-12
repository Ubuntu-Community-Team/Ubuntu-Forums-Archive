---
title: "Patchy data DVD detection?"
date: 2005-10-19
forum: General Help
---

### Post by pravda on 2005-10-19
I'm having a problem reading data DVD's. I've written them myself using k3b, with all 3 filesystems selected (Joliet, Rock Ridge and UDF). I did this because I was unable to read DVD's written with only Rock Ridge under Linux.

Anyway, I'll write a DVD, writing will complete successfully and the dvd will be ejected, then when I insert it in the drive (a DVD-RW drive), Ubuntu sometimes detects it as being a blank DVD. I'll remove it from the drive, wait 2 minutes and then insert it again, only to have ubuntu read the data on it with no trouble. Then I'll try again the next day and Ubuntu will be unable to read it. What the hell?

The relevant output from dmesg is:
[4397837.885000] cdrom: This disc doesn't have any tracks I recognize!

When I attempt to mount it as an ISO9660 device I get the following from dmesg:
[4398023.309000] attempt to access beyond end of device
[4398023.309000] hdc: rw=0, want=68, limit=4
[4398023.309000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

---

### Post by pravda on 2005-10-19
Another symptom: sometimes when I insert the DVD it complains about being unable to detect the fs type. Here is the output from dmesg in those cases:
<whole bunch of these, with different sector numbers>
[4398506.565000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4398506.565000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4398506.565000] ide: failed opcode was: unknown
[4398506.565000] end_request: I/O error, dev hdc, sector 64
<the last output is>
[4398506.578000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4398506.578000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4398506.578000] ide: failed opcode was: unknown
[4398506.578000] end_request: I/O error, dev hdc, sector 1024
[4398506.579000] UDF-fs: No partition found (1)

---

